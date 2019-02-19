<template>
    <div class="wrapper">
        <h1>Works 作品紹介</h1>
        <article v-for="d in data" :key="d.id"> <!--v-forでpropsで指定したdataを繰り返す-->
            <div>
                <ul v-for="p in d.picture" :key="p.id">
                    <li v-if="p.id === '1'"> <!--v-ifで写真の一枚目のみ呼び出し-->
                        <router-link :to="'/works/' + d.slug"><img :stc="p.path"></router-link>
                        <!--詳細へのリンクと画像のURL-->
                    </li>
                </ul>
            </div>
            <div>
                <h1 v-cloak><router-link :to="'/works/' + d.slug">{{ d.title }}</router-link></h1>
                <!--作品のタイトル-->
                <p class="product-description" v-cloak>{{ d.text }}</p> <!--作品の詳しめ解説-->
                <p class="product-year" v-cloak>制作年 : {{ d.year }}</p> <!--制作年-->
            </div>
        </article>
        WorksTopのページです。
    </div>
</template>

<script>
    export default {
        title: 'WorksTop',
        description: 'WorksTop',
        props: ['data']
    }
</script>