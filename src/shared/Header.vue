<template>
<div class="header">
    <a class="logo" href="#"><font-awesome-icon :icon="['fas', 'film']"/> </a>
    <a class="navicon" href="#"><font-awesome-icon :icon="['fas', 'heart']"/> </a>
    <a class="navicon" href="#"><font-awesome-icon :icon="['fas', 'shopping-cart']"/> </a>
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
  overflow:hidden;
}

.header-half {
  width: 50%;
}

.logo {
  float: left;
}


.navicon {
  float: right;
}
</style>
