<template>
  <div class="sidebar">
    <button class="flex"> Compose </button>
    <div @click="viewMailList" class="flex">Inbox ({{inboxCount}}) </div>
    <div class="flex">Important </div>
    <div class="flex">Sent Mail </div>
    <div class="flex">Drafts </div>
  </div>
</template>

<script>
export default {
  name: 'SideBar',
  props: ['inboxCount'],
  methods: {
    viewMailList: function () {
      this.$emit('viewMailList');
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.sidebar {
  display: flex;
  flex-direction: column;
  color:black;
  max-height: 1.5em;
  border-bottom: 1px solid #A8A8A8;
  padding: .2em 0 ;
  color: white;
  font-weight: 600;
  padding: 1.5rem;
  width: 130px;

  button.flex {
    text-transform: uppercase;
    font-size: 12px;
    text-align: center;
    padding: .6em 0;
    margin-bottom: 1em;
    text-transform: uppercase;
    width: 110px;
    margin-bottom: 1em;
  }

div.flex {
  flex: 1;
  max-height: 2em;
  display: flex;
  justify-content: center;
  flex-direction: column;


  &:hover {
    background-color: #4c4c4c;

  }

}
}
</style>
