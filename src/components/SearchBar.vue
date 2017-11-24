<template>
  <div class="search-bar-container flex">
    <input class="search-bar" type="text" name="search" >
    <a href="">
    <div class="search-button">
      <img class="search-icon" src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bd/VisualEditor_-_Icon_-_Search-big_-_white.svg/2000px-VisualEditor_-_Icon_-_Search-big_-_white.svg.png" />
    </div>
    </a>
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.search-bar-container {
  background-color: white;
  width: 500px;
  margin: .5em;

  .search-bar {
    width: calc(100% - 66px);
    height: 32px;
  }
  input[type="text"] {
    font-size:1.1em;
  }
  .search-button {
    background-color: #3C7BF4;
    width:60px;
    height: 100%;
    float: right;
    text-align: center;
    .search-icon {
      width: 2em;
      position: relative;
      top: 50%;
      transform: translateY(-50%);
    }
  }
}
</style>
