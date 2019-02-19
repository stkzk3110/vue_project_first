<template>
    <div class="wrapper">
        <article>
            <h1 v-cloak>{{ filteredData.title }}</h1> <!--作品タイトル -->
            <div>
                <ul v-for="p in filteredData.picture" :key="p.id">
                    <li v-if="p.id === '1'"> <!--v-ifで写真の一枚目のみ呼び出し-->
                        <img :src="p.path"> <!--画像のURL -->
                    </li>
                </ul>
            </div>
            <p v-cloak>{{ filteredData.text }}</p> <!-- 作品の詳しめ解説 -->
            <p v-cloak>制作年 : {{ filteredData.year }}</p> <!-- 制作年 -->
            <p v-cloak>{{ filteredData.role }}</p>
            <p v-cloak>
                <a :href="filteredData.url" target="_blank">{{ filteredData.urlTitle }}</a>
            </p> <!-- 参照URLとURLのタイトル -->
            <div>
                <ul v-for="p in filteredData.picture" :key="p.id">
                    <li v-if="p.id !== '1'"> <!-- v-ifで写真の一枚目以外を呼び出し -->
                        <img :src="p.path"> <!-- 画像のURL -->
                    </li>
                </ul>
            </div>
        </article>
        WorksDetailのページです。
    </div>
</template>

<script>
    export default {
        title: 'WorksDetail',
        description: 'WorksDetail',
        props: ['data'],
        computed: {
            filteredData: function() {
                var url = window.location.protocol + '//' + window.location.host + '/works/'
                var matchData = this.data.filter(function(item, index) {
                    if (item.slug === widnow.location.href.replace(url, '')) return true;
                })
                return matchData[0]
            }
        },
        mounted() {
            document.title = this.filteredData.title + `kyu-bu\'s portfolio`

            let meta = document.getElementsByTagName('meta')
            for (var i = 0; i < meta.length; i++) {
                if (meta[i].name.toLowerCase() == 'description') {
                    meta[i].content = 'kyu-buが作成した' + this.filteredData.title + 'のページです'
                }
            }
        }
    }
</script>