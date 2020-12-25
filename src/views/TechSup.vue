<template>
  <div class="techSup">
    <div class="max-w-2xl py-10 px-5 m-auto">
      <div class="text-3xl mb-6 text-center">
        We'll never help you, don't try it
      </div>

      <div class="grid grid-cols-2 gap-4 max-w-xl m-auto">
        <div class="col-span-2 lg:col-span-1">
          <input
            type="text"
            class="textBox md:text-xl"
            placeholder="Sender Name"
          />
        </div>
        <div class="col-span-2 lg:col-span-1">
          <input
            type="text"
            class="textBox md:text-xl"
            placeholder="Reciever Name"
            v-model="Res.recieverName"
          />
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
            @click="AddToAPI"
          >
            Submit
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      Message: {},
      Res: { userResName: "" },
    };
  },
  methods: {
    AddToAPI() {
    var senderName = sessionStorage.getItem("user");
    var recieverName = this.Res.recieverName;
    var senderID, recieverID;
    axios
      .get(
        "http://localhost:8081/stoom/user/getUserID?userName=" + senderName,
        {
          headers: {
            authorization: sessionStorage.getItem("authoruzation"),
          },
        }
      )
      .then((response) => {
        senderID = response.data[0].userResID;
      });
    axios
      .get(
        "http://localhost:8081/stoom/user/getUserID?userName=" + recieverName,
        {
          headers: {
            authorization: sessionStorage.getItem("authoruzation"),
          },
        }
      )
      .then((response) => {
        recieverID = response.data[0].userResID;
      });
      let Message = {
        messageRecieverUserID: recieverID,
        messageSenderUserID: senderID,
        messageText: this.Message.messageText,
      };
      axios
        .post("http://localhost:8081/stoom/message/", Message, {})
        .then((response) => {
          sessionStorage.setItem(
            "authorization",
            response.headers.authorization
          );

          console.log(response);
        });
    },
  },
};
</script>