<template>
    <div class="wrapper">
        <main>
            <form action="https://script.google.com/macros/s/AKfycbw_dXkx2oASgp4fJKsUeQQnHKVFDmVAVJKZB0QjsQcn3We5MxJX/exec" class="form-box">
                <input name="SPREADSHEET_ID" type="hidden" value="[id]">
                <input name="SHEET_NAME" type="hidden" value="フォームデータ">

                <h1>Contact お問い合わせ</h1>

                <div class="form-item-box">
                    <label class="control-label">Mail</label>
                    <div class="">
                        <input type="email" class="form-control" name="your-email" placeholder="your@email.com">
                    </div>
                </div>
                <div class="form-item-box">
                    <label class="control-label">お名前</label>
                    <div class="">
                        <input type="text" class="form-control" name="your-name" placeholder="YourName">
                    </div>
                </div>
                <div class="form-item-box">
                    <label class="control-label">メッセージ<span class="label-required">必須</span></label>
                    <div class="">
                        <textarea class="form-control" name="your-message" placeholder="Message" rows="8" required id="message"></textarea>
                    </div>
                </div>
                <div class="form-item-box">
                    <div class="form-button-box">
                        <button class="form-button" type="submit" v-on:click="sendMessage()">Submit</button>
                    </div>
                </div>
            </form>
        </main>
    </div>
</template>

<script>
    export default {
        title: 'Contact',
        description: 'きゅ〜ぶへのお問い合わせページ',
        methods: {
            sendMessage() {
                var form = $('form');
                var submitBtn = form.find('button[type=submit]');
                if (getElementById("message") === "") {
                    alert("メッセージを入力してください");
                    return false;
                }
                $.ajax({
                    url: form.attr('action'),
                    dataType: 'jsonp',
                    data: form.serialize(),
                    beforeSend: function() {
                        return submitBtn.prop('disabled', true);
                    },
                    complete: function() {
                        return submitBtn.prop('disabled', false);
                    },
                    jsonpCallback: 'console.log',
                    error: function(response) {
                        return console.log(response);
                    }
                });
            }
        }
    }
</script>