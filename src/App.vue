<style lang="scss">
  #app {
    .header {
      width : 100%;
      height: 60px;
      display: flex;
      position: fixed;
      top :0;
      padding: 20px 0px 10px 10px;
      align-items: center;
      justify-content: flex-start;
      background: white;

      .backspace-home {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        .backspace {
          margin-right: 20px;
          cursor: pointer;
        }
        .home {
          cursor: pointer;
        }
      }

      
      .header-text{
        display: inline-block;
        height: 30px;
        margin-right: auto;
        margin-left: auto;
        padding-right : 80px;
      }
    }
  }


  body {
    padding-top: 80px;
  }
</style>


<template>
  <div id="app">
    <div class="header">
      <div class="backspace-home">
        <div class="backspace" @click="goBack">
          <img src="./assets/icon-backspace.png">
        </div>
        <div class="home" @click="goHome">
          <img src="./assets/icon-home.png">
        </div>
      </div>

      <div class="header-text"> 기사 </div>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  methods : {
    goBack () {
      this.$router.go(-1);
    },

    goHome() {
      this.$router.push('/');
    }
  }
}
</script>