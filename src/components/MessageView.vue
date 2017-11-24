<template>
  <div class="message-view">
  <h3> {{message.subject}}  </h3>
  <div class="align-lr">
    <div class="sender-info">
      <img src="//ssl.gstatic.com/ui/v1/icons/mail/profile_mask_2x.png" style="background-color: #cccccc">
      <p class="sender"> {{message.sender}} </p>
    </div>
    <p class="date"> {{message.date.toDateString()}} </p>
  </div>
  <p class="body"> {{message.body}} </p>
</div>
</template>

<script>
export default {
  name: 'MessageView',
  props: ['message'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.message-view {
h3 {
  border-bottom: 1px solid #A8A8A8;
  padding: .5em .6em;
  font-weight: 400;
  margin-bottom: 0;
  margin-top: 0;
}
.align-lr {
  justify-content: space-between;
  display: flex;
  padding: 0 .7em;
  margin-top: .5em;
  .sender-info {
    display: flex;
    img {
      width: 30px;
      height: 30px;
      margin-right: 10px;
    }
    p {
      margin: 0;
      &.sender {
        font-weight: 600;
      }
    }
  }
  .date {
    margin-right: 40px;
    margin-bottom: 0;
    margin-top: 0;
  }
}
.body {
  padding: 0 3.2em;
  border-bottom: 1px solid #A8A8A8;
  padding-bottom: 3em;
}
}
</style>
