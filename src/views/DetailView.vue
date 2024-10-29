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

export default {
    name: 'DetailView',
    data() {
        return {
            article: null
        };
    }
};
</script>
