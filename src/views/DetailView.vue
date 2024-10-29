<template>
    <div class="article-detail" v-if="article">
        <figure>
            <img :src="article.image_url" alt="article-img"/>
        </figure>
        <h1>{{ article.title }}</h1>
        <p>{{ article.content }}</p>
        <span>{{ article.published_at }}</span>
    </div>
    <div v-else>
        <p>Loading...</p>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'DetailView',
    data() {
        return {
            article: []
        };
    },
    created() {
        this.fetchArticle();
    },
    methods: {
    async fetchArticle() {
        const { m, id } = this.$route.params;
        console.log('Fetching article with m:', m, 'and id:', id); 
        try {
            const response = await axios.get(`https://react-server-ykb.vercel.app/news?m=${m}`);
            this.article = response.data.data.find(article => article.id === id);
            
            if (!this.article) {
                console.error(`Article with ID ${id} not found in the response`);
            }
        } catch (error) {
            console.error('Failed to fetch article:', error);
        }
    }
}

};
</script>

