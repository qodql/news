<template>
    <div class="search-list">
        <h3>검색</h3>
        <input type="text" v-model="keyword" placeholder="검색어를 입력하세요" @keyup.enter="searchArticles" />
        <div class="results-contents">
            <div v-for="v in item" :key="v.id" class="results-content">
                <figure>
                    <img :src="v.thumbnail_url" alt="search-img" />
                </figure>
                <div>
                    <p>{{ v.title }}</p>
                    <span>{{ v.published_at }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'SearchList',
    data() {
        return {
            keyword: '',
            item: [],
        };
    },
    methods: {
        async searchArticles() {
            const m = 'articles';

            if (!this.keyword) return;

            try {
                const res = await axios.get(`http://localhost:4000/news/search?m=${m}&keyword=${this.keyword}`);
                console.log(res.data);
                this.item = res.data.data;
            } catch (error) {
                console.error('검색 요청 오류:', error);
            }
        },
    },
};
</script>

<style lang="scss">
.search-list {
    h3{
        font-size: 18px;
        color: #111;
    }
    input {
        width: 100%;
        padding: 12px;
        margin: 12px 0;
        border-radius: 8px;
        border: 1px solid #666;
    }
    .results-contents{
        .results-content {
            margin: 16px 0;
            display: flex;
            gap: 16px;
            figure{
                width: 160px;
                height: 106px;
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
</style>
