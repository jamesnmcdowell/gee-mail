<template>
  <div id="app">
    <header>
      <div class="header1 flexbox-container">
        <h1 class="flex"> Gee-Mail </h1>
        <SearchBar />
      </div>
      <div class="header2">
        <button @click="refresh"> click me </button>
        <button @click="pushMail"> push me </button>
      </div>
    </header>

    <div class="flexbox-container">
    <SideBar class = "sidebar" :inboxCount="mail.length"    />
    <article class="main">
    <div class="mail-container">
    <div v-if="selectedMail !== undefined">
      <h1> sup bitch </h1>

    </div>
    <div v-else>
      <MailRow @click="openEmail(data)" v-for="data in mail" key="data.time" :rowData="data" />
    </div>

    </div>
    </article>
  </div>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import MailRow from './components/MailRow'
import SideBar from './components/SideBar'
import SearchBar from './components/SearchBar'
import {mailGenerator, singleMailGenerator} from './mail-generator.js'
let genMail = mailGenerator();
console.log(genMail);
export default {
  name: 'app',
  components: {
    HelloWorld,
    MailRow,
    SideBar,
    SearchBar
  },
  data () {
    return {
      mail: genMail,
      selectedMail: undefined,
    }
  },
  methods: {
    refresh: function () {
      this.mail = mailGenerator();
    },
    pushMail: function () {
      this.mail.push(singleMailGenerator());
    },
    openEmail: function (data) {
      console.log("hi");
      this.selectedMail = data;
    }
  }
}
</script>

<style lang="scss">
html, body{
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
}
header{
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
  }

}

.flexbox-container{
	display: flex;
	width: 100%;
}
.sidebar{
	order: 1;
	flex: 0 0 200px;
  flex-basis: auto;
  padding: .5rem;
  min-height: 666px;

}
.main{
	order: 1;
	flex: 5;
}

.mail-container {
  margin-right: 2em;
}
#app {
  background-image: url('https://brushbucktours.com/wp-content/uploads/2015/01/mormon-row.jpg') ;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  width: 100%;
  height: 100%;
}
</style>
