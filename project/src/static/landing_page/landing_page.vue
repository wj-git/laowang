<template>
<div>
        <div v-wechat-title="$route.meta.title"></div>
        <div class="page_wrap">
        <h3>老庙黄金，给您带来好运气</h3>
        <ul>
            <li>
                <img src="./img/49476653903732260.png" alt="">
                <p>老庙黄金的每件首饰都是福瑞，蕴含着百年的祥瑞与好运。</p>
            </li>
            <li>
                <img src="./img/49476653903732260.png" alt="">
                <p>老庙黄金的每件首饰都是福瑞，蕴含着百年的祥瑞与好运。老庙黄金的每件首饰都是福瑞，蕴含着百年的祥瑞与好运。</p>
            </li>
        </ul>
        <div class="page_address">
            <div class="page_address_text">
                <div style="width: 100%;height: 0.7rem;">
                    <img src="./img/address.png" alt="">
                    <p>海德花园南门东行50米</p>
                </div>
                <div style="width: 100%;height: 0.7rem;">
                    <img style="width: 0.4rem;height: 0.4rem;" src="./img/tel.png" alt="">
                    <p>1111111</p>
                </div>
                <div class="page_like">
                    <img src="./img/Fill 1.png" alt="" v-show="show_like">
                    <p v-show="show_like">感兴趣</p>
                    <img src="./img/share.png" alt="" v-show="show_share">
                    <p v-show="show_share">分享</p>
                </div>
            </div>
        </div>
    </div>
    <div class="page_btn">
        <div>一键咨询</div>
        <div>我已阅读</div>
    </div>
</div>
</template>

<script>
export default {
    data(){
        return {
            show_share: true,
            show_like: false
        }
    }
}
</script>

<style>
@import './css/landing_page.css';
</style>


