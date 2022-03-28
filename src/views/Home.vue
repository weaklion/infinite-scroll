<style lang="scss">
  
  .news-list {
    height:100%;
    margin:20px;
    display:flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  
  }
  
  
 
</style>


<template>
  <div class="container">
    <!-- component -->
    <div 
      class="news-list"
      v-for="item in items"
      :key="item.id"
    >
      <Article :item="item" />
    </div>
    <Observer @intersect="intersected" />
  </div>
</template>

<script>

import Article from '../components/Article.vue';
import Observer from '../components/Observer.vue';


export default {
  name: 'App',
  data () {
    return {
      page : 1,
      items : [],
      scrollPosition : 0,
    }
  },

  methods : {
    async intersected() {
      const res = await fetch(`https://jsonplaceholder.typicode.com/photos?_page=${this.page}&_limit=10`);
      this.page++;
      const items = await res.json();
      const nowScrollPosition = window.scrollY || document.documentElement.scrollTop;
      const resultItems = [...this.items, ...items];
      this.items = resultItems;
      this.scrollPosition = nowScrollPosition;
      
      sessionStorage.setItem("page", JSON.stringify({
        "pageCount" : this.page,
        "items" : resultItems,
        "scrollPosition" : nowScrollPosition
      }));
    }
  },

  mounted() {
    if(sessionStorage.getItem('page')) {
      const sessionData = JSON.parse(sessionStorage.getItem('page'));
      this.page = Number.parseInt(sessionData.pageCount); 
      this.items = sessionData.items;
      this.scrollPosition = Number.parseInt(sessionData.scrollPosition);
      window.scrollTo(0, this.scrollPosition);
    }
  },

  components : {
    Article,
    Observer
  }

}
</script>

