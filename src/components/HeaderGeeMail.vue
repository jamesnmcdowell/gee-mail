<template>
  <header>
    <div class="header1 flexbox-container">
      <h1 class="flex"> Gee-Mail </h1>
      <SearchBar />
    </div>
    <div class="header2">
      <button @click="refresh"> Refresh </button>
      <button @click="pushMail"> Add Email </button>
      <button @click="resetSelectedMail"> Back </button>
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

header {
  color: white;
  font-weight: 600;
  .header1 {
    border-bottom: 1px solid #A8A8A8;
    padding: .5rem;
    h1 {
      margin: 0;
      padding-right: 2em;
    }
  }
  .header2 {
    border-bottom: 1px solid #A8A8A8;
    padding: 1rem;
    display: flex;

    button {
      font-size: 12px;
      margin-right: .5em;
      text-align: center;
      padding: .6em 0;
      margin-bottom: 1em;
      width: 100px;
    }
  }
}
</style>
