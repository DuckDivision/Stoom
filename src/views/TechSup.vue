<template>
  <div class="techSup">
    <div class="techSupMessages">
    <h2 class="max-w-xl py-3 px-5 m-auto text-2xl">Message history: </h2>
    <ul class="max-w-xl py-5 px-5 m-auto bg-blue-100" style="overflow-y: auto; max-height: 400px">
      <li v-for="message in messages" v-bind:key="message.messageResID">
          <b v-if="message.messageResSenderUser == user">{{message.messageResSenderUser}}:</b> 
          <b v-else><i>you:</i></b> 
          {{message.messageResText}}
          <br>
        </li>
      </ul>
    </div>
    <div class="max-w-2xl py-10 px-5 m-auto">
      <div class="text-3xl mb-6 text-center">We'll never help you, don't try it</div>

      <div class="grid grid-cols-2 gap-4 max-w-xl m-auto">
        <div class="w-full py-1 px-2 bg-blue-100">
          <p style="color:#000000">Sensei listen you</p>
        </div>
        <div class="col-span-2">
          <textarea
            cols="30"
            rows="8"
            class="textBox md:text-xl"
            placeholder="Cry me a river"
            v-model="Message.messageText"
          ></textarea>
        </div>
        <div class="col-span-2 text-right">
          <button
            class="py-3 px-6 bg-green-500 text-white font-bold w-full sm:w-32"
            @click="AddMess"
          >Submit</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";  
var senderID;
var recieverID = "793cf14b-a2c8-4fff-910d-1fbca4e09127";
export default {
  components: { },
  data() {
    return {
      Message: {},
      Res: {},
      messages: undefined,
      user: sessionStorage.getItem('user')
    };
  },
  methods: {
    AddMess() {
      let Message = {
        messageRecieverUserID: recieverID,
        messageSenderUserID: senderID,
        messageText: this.Message.messageText
      };
      console.log(recieverID, senderID, this.Message.messageText);
      axios
        .post("http://localhost:8081/stoom/message/", Message, {
          headers: {
            authorization: sessionStorage.getItem("authorization")
          }
        })
        .then(responze => {
          console.log(responze);
        });
    }
  },
  mounted() {
    var senderName = sessionStorage.getItem("user");

    //var recieverName = "f";
    console.log("??");
    console.log(senderName);

    axios
      .get("http://localhost:8081/stoom/user/getUserID", {
        params: {
          userName: sessionStorage.getItem("user")
        },
        headers: {
          authorization: sessionStorage.getItem("authorization")
        }
      })
      .then(response => {
        senderID = response.data.userResID;
        console.log(senderID);
      });
      axios.get("http://localhost:8081/stoom/user/", {
            params : {
                userName: sessionStorage.getItem("user")
            },
            headers: {
                authorization: sessionStorage.getItem("authorization")
            }
        })
        .then(response => {
            let userKey = response.data[0].userResID;
            axios.get("http://localhost:8081/stoom/message/", {
                params : {
                    userID: userKey
                },
                headers: {
                    authorization: sessionStorage.getItem("authorization")
                }
            })
            .then(response => {
                this.messages = response.data.reverse()     
             });
        });
  }
};
</script>