<template>
  <header>
    <div class="header1 flexbox-container">
      <h1 class="flex"> Gee-Mail </h1>
      <SearchBar />
    </div>
    <div class="header2">
      <button @click="refresh"> click me </button>
      <button @click="pushMail"> push me </button>
      <button @click="resetSelectedMail"> back </button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'HeaderGeeMail',
  methods: {
    refresh: function () {
      this.$emit('refresh');
    },
    pushMail: function () {
      this.$emit('pushMail');
    },
    resetSelectedMail: function () {
      this.$emit('resetSelectedMail');
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>


</style>
