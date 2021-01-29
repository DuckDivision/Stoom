<template>
  <div id="app">
    <!--Navigation-->
    <div class="py-4 px-20 bg-yellow-500">
      <!--Small screen drop-button-->
      <div class="flex items-center md:hidden">
        <button @click="isVisible = !isVisible">
          <svg
            class="cursor-pointer items-center w-6 h-6"
            fill="none"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            stroke="currentColor"
            viewBox="0 0 24 24"
          >
            <path d="M4 6h16M4 12h16M4 18h16"></path>
          </svg>
        </button>
        <span class="mx-auto text-2xl">Stoom</span>
      </div>
      <!--Small screen drop-menu-->
      <div
        class="md:hidden flex flex-col divide-y-2 divide-gray-800 text-center text-2xl mt-4"
        v-if="isVisible"
      >
        <router-link to="/">Store</router-link>
        <router-link to="/Library">Library</router-link>
        <router-link to="/TechSup">Help</router-link>
        <div class="divide-x-2 divide-gray-800">
          <router-link v-if="!isLoggedIn()" to="/Login" class="px-10">Login</router-link>
          <router-link v-if="!isLoggedIn()" to="/SignUp" class="px-10">SignUp</router-link>
          <router-link v-if="isLoggedIn()" to="/Profile">Profile</router-link>
          <a @click="logout" v-if="isLoggedIn()">Logout</a>
        </div>
      </div>
      <!--Navigation menu-->
      <nav class="hidden md:block">
        <div class="flex justify-between items-center text-2xl">
          <div class="flex divide-x-2 divide-gray-800">
            <svg
              class="mx-2 w-10 h-10"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M11 4a2 2 0 114 0v1a1 1 0 001 1h3a1 1 0 011 1v3a1 1 0 01-1 1h-1a2 2 0 100 4h1a1 1 0 011 1v3a1 1 0 01-1 1h-3a1 1 0 01-1-1v-1a2 2 0 10-4 0v1a1 1 0 01-1 1H7a1 1 0 01-1-1v-3a1 1 0 00-1-1H4a2 2 0 110-4h1a1 1 0 001-1V7a1 1 0 011-1h3a1 1 0 001-1V4z"
              ></path>
            </svg>
            <router-link to="/" class="px-2 hover:bg-blue-500"
              >Store</router-link
            >
            <router-link to="/Library" class="px-2 hover:bg-blue-500"
              >Library</router-link
            >
            <router-link to="/TechSup" class="px-2 hover:bg-blue-500"
              >Tech support</router-link
            >
          </div>
          <div class="flex divide-x-2 divide-gray-800">
            <router-link to="/Login" class="px-2 hover:bg-blue-500"
              v-if="!isLoggedIn()"
              >Login</router-link
            >
            <router-link to="/SignUp" class="px-2 hover:bg-blue-500"
              v-if="!isLoggedIn()"
              >SignUp</router-link
            >
            <router-link to="/Profile" class="px-2 hover:bg-blue-500"
              v-if="isLoggedIn()"
              >Profile</router-link
            >
            <a class="px-2 hover:bg-blue-500"
              v-if="isLoggedIn()"
              @click="logout"
              >Logout</a
            >
          </div>
        </div>
      </nav>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: "stoom-nav",
  props: {},
  data: () => {
    return {
      isVisible: false,
    };
  },
  methods: {
    isLoggedIn: function() {
      return sessionStorage.getItem('role') != null;
    },
    logout: function() {
        sessionStorage.clear();
        this.$forceUpdate();
        this.$router.push('/');
    }
  },
};
</script>