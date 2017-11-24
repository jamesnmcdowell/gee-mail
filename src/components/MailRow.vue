<template>
  <div class="row">
    <label class="container">
      <input type="checkbox" >
      <span class="checkmark"></span>
    </label>
    <div @click="callSelectMail" class="row">
      <div class="flex sender">{{ rowData.sender }} </div>
      <div class="flex subject">{{ rowData.subject}} </div>
      <div class="flex body">{{ rowData.body }} </div>
      <div class="flex date">{{ rowData.date.toDateString() }} </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MailRow',
  props: ['rowData'],
  methods: {
    processDate: function (rowData) {
      var s = rowData.date;
      console.log(typeof s);
      console.dir(s);
      var n = s.indexOf('T');
      s = s.substring(0, n != -1 ? n : s.length);
      return s;
    },
    callSelectMail: function () {
      this.$emit('selectMail',this.rowData);
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
.row {
  display: flex;
  flex-direction: row;
  background-color: rgba(235, 237, 241, .8);
  color:black;
  max-height: 1.5em;
  border-bottom: 1px solid #A8A8A8;
  padding: .2em 0 ;
  padding-left: 1.5em;

  label {
    justify-content: center;
    flex-direction: column;
    display: flex;
    &.container {
        margin-top: 4px;
    }
  }

  .flex {
    flex: 1;
    overflow: hidden;
  }
}



.container {
    display: block;
    position: relative;
    padding-left: 35px;
    cursor: pointer;
    font-size: 22px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    &:hover input ~ .checkmark {
        background-color: #ccc;
    }
    input:checked ~ .checkmark {
        background-color: #2196F3;
    }
    input:checked ~ .checkmark:after {
        display: block;
    }
    input {
        position: absolute;
        opacity: 0;
    }
    .checkmark {
        position: absolute;
        top: 0;
        left: 0;
        height: 15px;
        width: 15px;
        background-color: #eee;
        &:after {
          content: "";
          position: absolute;
          display: none;
          left: 4px;
          top: 0px;
          width: 4px;
          height: 9px;
          border: solid white;
          border-width: 0 3px 3px 0;
          -webkit-transform: rotate(45deg);
          -ms-transform: rotate(45deg);
          transform: rotate(45deg);
        }
    }
}
</style>
