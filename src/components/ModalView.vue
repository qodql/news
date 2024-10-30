<template>
    <div class="modal-overlay" @click.self="close">
      <div class="modal-content">
        <!-- <button class="close-button" @click="close">✕</button> -->
        <p class="modal-section">{{ sectionName }}</p>
        <h4>{{ article.title }}</h4>
        <p class="modal-date">{{ article.published_at }}</p>
        <img :src="article.image_url" alt="article image" />
        <p class="modal-summary">{{ article.summary }}</p>
      </div>
    </div>
</template>
  
<script>
  export default {
    props:{ 
      article: Object
    },
    computed:{
        sectionName() {
            const sectionText = {
                economy: '경제',
                culture: '문화',
                politics: '정치',
                entertainment: '연예'
            };
            return sectionText[this.article.sections] || this.article.sections;
        }
    },
    methods: {
      close() {
        this.$emit('close');
      }
    }
  };
</script>
  
<style lang="scss">
  .modal-overlay{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.1);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 99;
    .modal-content{
      background-color: #fff;
      padding: 40px 20px;
      border-radius: 8px;
      max-width: 480px;
      width: 100%;
      height: 600px;
      overflow-y: auto;
      position: relative;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      .modal-section{
        width: 60px;
        height: 28px;
        line-height: 28px;
        color: #525a7e;
        background-color: #dddfeb;
        border-radius: 16px;
        text-align: center;
        font-size: 16px;
        font-weight: 600;
        margin-bottom: 12px;
      }
      h4{
        border: 1px dashed #333;
        border-left: none;
        border-right: none;
        font-size: 20px;
        color: #111;
        padding: 16px 0;
        margin-bottom: 8px;
      }
      .modal-date{
        color: #666;
        font-size: 12px;
        margin-bottom: 24px;
      }
      img{
        width: 100%;
        border-radius: 8px;
      }
      .modal-summary{
        color: #333;
        font-size: 16px;
        margin: 28px 0;
      }
      .close-button{
        position: absolute;
        top: 15px;
        right: 15px;
        background: transparent;
        border: none;
        font-size: 20px;
        cursor: pointer;
        color: #555;
      }
    }
  }
</style>
  