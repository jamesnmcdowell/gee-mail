<template>
  <div id="app">
   <HeaderGeeMail @refresh="refresh" @pushMail="pushMail" @resetSelectedMail="resetSelectedMail" />
    <div class="flexbox-container">
      <SideBar @viewMailList="resetSelectedMail" class = "sidebar" :inboxBack="resetSelectedMail" :inboxCount="mail.length"/>
      <article class="main">
        <div class="mail-container">
          <div  v-if="selectedMail !== undefined" class="mail-view" v-bind:class="{ active: isActive }">
            <MessageView :message="selectedMail" />
          </div>
          <div v-else>
            <MailRow @selectMail="setSelectedMail" v-for="data in mail" key="data.time" :rowData="data" />
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
import MessageView from './components/MessageView'
import HeaderGeeMail from './components/HeaderGeeMail'
import {mailGenerator, singleMailGenerator} from './mail-generator.js'
let genMail = mailGenerator();

export default {
  name: 'app',
  components: {
    HelloWorld,
    MailRow,
    SideBar,
    SearchBar,
    MessageView,
    HeaderGeeMail

  },
  data () {
    return {
      mail: genMail,
      selectedMail: undefined,
      isActive: true,
    }
  },
  methods: {
    //refresh emails
    refresh: function () {
      this.mail = mailGenerator();
    },
    //add random email to inbox (add row)
    pushMail: function () {
      this.mail.push(singleMailGenerator());
    },
    //store email data when opening email to show email expanded view
    setSelectedMail: function (data) {
      this.selectedMail = data;
    },
    //reset email data when leaving inbox to show email list view
    resetSelectedMail: function (data) {
      this.selectedMail = undefined;
    },
    processDate: function (rowData) {
          var s = rowData.date;
          console.log(typeof s);
          console.dir(s);
          var n = s.indexOf('T');
          s = s.substring(0, n != -1 ? n : s.length);
          return s;
        },
  }
}
</script>

<style lang="scss">
html, body {
	margin: 0;
	padding: 0;
	width: 100%;
	overflow-x: hidden;
	#app {
		background-image: url('https://brushbucktours.com/wp-content/uploads/2015/01/mormon-row.jpg');
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
			}
		}
		.flexbox-container {
			display: flex;
			width: 100%;
			.sidebar {
				order: 1;
				flex: 0 0 200px;
				flex-basis: auto;
				padding: .5rem;
				min-height: 666px;
			}
			.main {
				order: 1;
				flex: 5;
				.mail-container {
					margin-right: 2em;
					.active {
						height: 100vh;
						background-color: #FFFFFF;
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
				}
			}
		}
	}
}
</style>
