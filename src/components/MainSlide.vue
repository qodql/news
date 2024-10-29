<template>
    <div class="main-slide">
      <swiper 
        :slides-per-view="1.2" 
        :space-between="16" 
        :centered-slides="true" 
        :pagination="true" 
        :loop="true"
        class="mySwiper">
            <swiper-slide v-for="article in articles" :key="article.id">
            <div class="main-img" :style="{ backgroundImage: `url(${article.image_url})` }"></div>
            <div class="main-title">
                <article>
                <h3>{{ article.title }}</h3>
                </article>
            </div>
            </swiper-slide>
        </swiper>
    </div>
</template>
  
<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/swiper-bundle.css';
import axios from 'axios';
  
export default{
    name: 'MainSlide',
    components:{
        Swiper,
        SwiperSlide,
    },
    data() {
      return {
        articles: [],
      };
    },
    created() {
      this.fetchArticles();
    },
    methods: {
      async fetchArticles() {
        try {
          const response = await axios.get('https://react-server-ykb.vercel.app/news?m=articles&s=culture');
          this.articles = response.data.data;
        } catch (error) {
          console.error('Error fetching articles:', error);
        }
      }
    }
  };
</script>
  
<style lang="scss">
  .main-slide {
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
      .swiper-slide-prev, .swiper-slide-next {
        transition: 0.5s;
        position: relative;
          .main-img {
            position: absolute;
            top: 20px;
            height: 220px;
          }
      }
      .main-img {
          width: 100%;
          height: 240px;
          background-size: cover;
          background-position: center;
          border-radius: 4px;
      }
      .main-title {
          width: 100%;
          article {
              padding: 20px 0;
              h3 {
                  font-size: 18px;
                  font-weight: 600;
                  color: #111;
                  word-break: keep-all;
              }
          }
      }
  }
  </style>
  