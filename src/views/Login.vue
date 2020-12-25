<template>
  <div class="login">
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
          <router-link to="/Profile">
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="button"
              @click="AddToAPI"
            >Log In</button>
          </router-link>
          <router-link to="/TechSup">
            <button
              class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800"
            >Forgot Password?</button>
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
      let User = {
        userPassword: this.User.userPassword,
        userReqName: this.User.userReqName
        
      };
      console.log(User);
      axios
        .post("http://localhost:8081/stoom/user/authUser", User)
        .then(response => {
          sessionStorage.setItem(
            "authorization",
            response.headers.authorization
          );
          sessionStorage.setItem("user", User.userReqName);
          sessionStorage.setItem("role", response.headers["user-role"]);
          
          console.log(response);
        });
    }
  }
};
</script>