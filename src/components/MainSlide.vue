<template lang="">
    <div class="main-slide">
        <div class="main-img"></div>
        <div class="main-title">
            <article>
                <h3>[1보] 오태완 의령군수·이장우 경남도의원 항소심 불복, 대법원 상고</h3>
            </article>
        </div>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss">
    .main-slide{
        width: 100%;
        height: 100%;
        position: relative;
        &::after {
            width: calc(100% + 32px);
            height: 6px;
            margin-left: -16px;
            margin-right: -16px;
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            background-color: #f2f2f2;
        }
        .main-img{
            width: calc(100% + 32px);
            height: 240px;
            background: url('../../public/img/main-slide01.jpg') no-repeat center;
            margin-left: -16px;
            margin-right: -16px;
        }
        .main-title{
            width: 100%;
            article{
                padding: 20px 0;
                h3{
                    font-size: 18px;
                    font-weight: 600;
                    color: #111;
                    word-break: keep-all;
                }
            }
        }
    }
</style>