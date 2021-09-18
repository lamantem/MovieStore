<template>
<div class="header">
  <div class="header-half left">
    <a href="#">Logo</a>
  </div>
  <div class="header-half right">
    <a href="#">Favs</a>
    <a href="#">aaa </a>
  </div>
</div>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
  padding: 14px;
  background-color: aquamarine;
  overflow:hiden;
}

.header-half {
  width: 50%;
}

.left {
  float: left;
}


.right {
  float: right;
}
</style>
