<template>
  <div class="signUp">
    <div class="py-10 max-w-md mx-auto">
      <form class="bg-white shadow-xl rounded px-8 pt-6 pb-8 mb-4">
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="username">User</label>
          <input
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            id="username"
            type="text"
            placeholder="Username"
            v-model="User.userReqName"
          />
        </div>
        <div class="mb-6">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="password">Password</label>
          <input
            class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
            id="password"
            type="password"
            placeholder="******************"
            v-model="User.userPassword"
          />
        </div>
        <div class="flex items-center justify-between">
          <router-link to="/Login">
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="button"
              @click="AddToAPI"
            >Sign up</button>
          </router-link>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      User: { userPassword: "", userReqName: "" }
    };
  },

  methods: {
    AddToAPI() {
      let newUser = {
        userPassword: this.User.userPassword,
        userReqName: this.User.userReqName
      };
      console.log(newUser);
      axios
        .post("http://localhost:8081/stoom/user/registerUser", newUser)
        .then(response => {
          console.log(response);
        });
      
    }
  }
};
</script>