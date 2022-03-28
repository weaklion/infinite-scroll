
<style lang="scss">
  .article-container {
    width : 335px;
    height : 74px;
    display: flex;
    flex-direction: row;
    margin-bottom: 12px;


    .article {
      margin-right: 10px;
      .title {
        font-weight: 500;
        font-size: 16px;
        line-height: 24px;
        letter-spacing: -0.4px;
        width: 240px;
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-line-clamp: 2; /* 라인수 */
        -webkit-box-orient: vertical;
        word-wrap:break-word; 
        line-height: 1.2em;
        height: 2.4em; 
        margin-bottom: 4px;
      }
    }

    .press-time {
      display: flex;
      height: 20px;

      .press, .time {
        margin-right: 10px;
        color: #A0A0A0;
        font-size: 14px;
        line-height: 20px;
        font-weight: 14px;
        letter-spacing: -0.4px;
      }
    }

    .news-image {
      border: 1px solid rgba(0,0,0,0.04);
      box-sizing: border-box;
      border-radius: 8px;
      overflow: hidden;
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    } 
  }


</style>


<template>
  <div class="article-container" @click="clickArticle">
    <div class="article"> 
      <div class="title">
        {{item.title}}
      </div>

      <div class="press-time">
        <div class="press"> 경향신문</div>
        <div class="time"> 4시간 전</div>
      </div>
    </div>

    <div class="news-image">
      <img :src="item.thumbnailUrl">
    </div>

  </div>  
</template>

<script>
export default {
  props : {
    item : null,
  },

  methods : {
    clickArticle() {
      this.$router.push({
        name : 'Detail',
        params : { title : this.item.title }
      })
    }
  }
}
</script>
