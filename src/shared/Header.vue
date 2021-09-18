<template>
<div class="header">

  <div id="column1">
     <a class="logo" href="#">
      <font-awesome-icon class="oops" :icon="['fas', 'film']" transform="grow-6"  fixed-width /> 
    </a>
  </div>

  <div id="column2">
    <input class="search-field" type="text" placeholder="Search title.."/>
  </div>

  <div id="column3">
     <font-awesome-icon class="navicon oops" 
    :icon="['fas', 'heart']" transform="grow-6"  fixed-width />
      <font-awesome-icon class="navicon oops" 
      :icon="['fas', 'shopping-cart']" transform="grow-6"  fixed-width />
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
  background-color: #7fe4d5;
  overflow:hidden;
  display: flex;
}

.header > div {
  flex-grow: 1;
}

#column1, #column3 {
  width: 25%;
  display: inline-block;
}

#column2 {
  width: 50%;
  display: inline-block;
}

.search-field {
  width: 100%;
}
.logo {
  float: left;
}

.navicon {
  float: right;
}

.oops {
  margin: 0 8px 0 8px;
}
</style>
