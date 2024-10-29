<template lang="">
    <div class="domestic">
        <div>
            <div class="domestic-tab">
                <button @click="tabName = 'all'; apiRequest()" :class="{ active: tabName === 'all' }">전체</button>
                <button @click="tabName = 'economy'; apiRequest()" :class="{ active: tabName === 'economy' }">경제</button>
                <button @click="tabName = 'culture'; apiRequest()" :class="{ active: tabName === 'culture' }">문화</button>
                <button @click="tabName = 'politics'; apiRequest()" :class="{ active: tabName === 'politics' }">정치</button>
                <button @click="tabName = 'entertainment'; apiRequest()" :class="{ active: tabName === 'entertainment' }">연예</button>
            </div>
            
            <div class="domestic-contents">
                <div v-if="tabName === 'all'">
                    <div v-for='v in filteredItems' :key='v.id' class="domestic-content" @click="moveDetail(v)">
                        <figure>
                            <img :src="v.thumbnail_url" alt="domestic-img"/>
                        </figure>
                        <div>
                            <p>{{v.title}}</p>
                            <span>{{v.published_at}}</span>
                        </div>
                    </div>
                </div>
                <div v-else-if="tabName === 'economy'">
                    <div v-for='v in filteredItems' :key='v.id' class="domestic-content">
                        <figure><img :src="v.thumbnail_url" /></figure>
                        <div>
                            <p>{{v.title}}</p>
                            <span>{{v.published_at}}</span>
                        </div>
                    </div>
                </div>
                <div v-else-if="tabName === 'culture'">
                    <div v-for='v in filteredItems' :key='v.id' class="domestic-content">
                        <figure><img :src="v.thumbnail_url" /></figure>
                        <div>
                            <p>{{v.title}}</p>
                            <span>{{v.published_at}}</span>
                        </div>
                    </div>
                </div>
                <div v-else-if="tabName === 'politics'">
                    <div v-for='v in filteredItems' :key='v.id' class="domestic-content">
                        <figure><img :src="v.thumbnail_url" /></figure>
                        <div>
                            <p>{{v.title}}</p>
                            <span>{{v.published_at}}</span>
                        </div>
                    </div>
                </div>
                <div v-else-if="tabName === 'entertainment'">
                    <div v-for='v in filteredItems' :key='v.id' class="domestic-content">
                        <figure><img :src="v.thumbnail_url" /></figure>
                        <div>
                            <p>{{v.title}}</p>
                            <span>{{v.published_at}}</span>
                        </div>
                    </div>
                </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'DomesticArticle',
    props: ['m'],
    watch: {
        m: {
            immediate: true,
            handler() {
                this.apiRequest();
            }
        }
    },
    data() {
        return {
            tabName: 'all',
            item: []
        }
    },
    computed: {
        filteredItems() {
            return this.item.filter(v => v.thumbnail_url).slice(0, 4);
        }
    },
    created(){
        this.apiRequest();
    },
    methods: {
        async apiRequest() {
            const s = this.tabName === 'all' ? 'economy,culture,politics,entertainment' : this.tabName;
            try {
                const res = await axios.get(`https://react-server-ykb.vercel.app/news?m=${this.m}&s=${s}`);
                console.log(res.data);
                this.item = res.data.data;
            } catch (error) {
                console.error('API 요청 오류:', error);
            }
        },
        moveDetail(article)  {
            this.$router.push({
                name: 'DetailView',
                params: { id: article.id }
            });
        }
    }
}
</script>

<style lang="scss">

.domestic{
    margin: 20px 0;
    div{
        .domestic-tab{
            display: flex;
            gap: 4px;
            button{
                width: 60px;
                height: 28px;
                line-height: 28px;
                border: 1px solid #333;
                border-radius: 16px;
                background-color: transparent;
                font-size: 12px;
                color: #333;
                &.active{
                    background-color: #007BFF;
                    border: none;
                    color: #fff;
                }
            }
        }
        .domestic-contents{
            .domestic-content{
                margin: 16px 0;
                display: flex;
                gap: 16px;
                figure{
                    width: 160px;
                    height: 106px;
                    border-radius: 4px;
                    img{
                        width: 160px;
                        height: 106px;
                        border-radius: 4px;
                    }
                }
                div{
                    display: flex;
                    flex-direction: column;
                    position: relative;
                    p{
                        font-size: 14px;
                        font-weight: 600;
                        color: #111;
                        margin-top: 16px;
                    }
                    span{
                        position: absolute;
                        bottom: 8px;
                        font-size: 12px;
                        font-weight: 300;
                        color: #666;
                    }
                }
            }
        }
    }
}

</style>
