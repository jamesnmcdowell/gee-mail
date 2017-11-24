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

</style>
