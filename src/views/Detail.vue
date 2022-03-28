<style lang="scss">
  .detail-container {
    display: flex;
    justify-content: center;
  
  }
</style>

<template>
  <div class="detail-container">
    {{$route.params.title}}
  </div>  
</template>

<script>
export default {
  
}
</script>