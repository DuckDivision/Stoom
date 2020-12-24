<template>
  <div class="prof">
    <div>
      <main>
        <div class="w-full relative overflow-hidden">
          <div class="top h-64 w-full overflow-hidden relative">
            <img
              src="https://images.alphacoders.com/106/thumb-1920-1062752.jpg"
              alt
              class="bg w-full h-full object-cover object-center absolute z-0"
            />
            <div
              class="flex flex-col justify-center items-center relative h-full bg-black bg-opacity-25 text-white"
            >
              <img
                src="https://cdn.frankerfacez.com/emoticon/405548/4"
                class="h-24 w-24 object-cover"
              />
              <h2 class="text-2xl">Turtle pepega</h2>
              <h4 class="text-sm">WEB DEV GOOD</h4>
            </div>
          </div>
          <div class="grid grid-cols-12">
            <div
              class="col-span-12 w-full px-3 py-6 justify-center flex space-x-4 md:space-x-0 md:space-y-4 md:flex-col md:col-span-2 md:justify-start"
            >
              <router-link to="/Prof" class="text-sm p-2 text-center bg-yellow-500">Information</router-link>
              <router-link to="/profSettings" class="text-sm p-2 text-center">Settings</router-link>
              <router-link to="/addGame" class="text-sm p-2 text-center">Add new game</router-link>
              <router-link to="/addPromo" class="text-sm p-2 text-center">Promotion</router-link>
            </div>
            <div
              class="col-span-12 md:border-solid md:border-l md:border-black md:border-opacity-25 h-full pb-12 md:col-span-10"
            >
              <div class="px-4 pt-4">
                <form action="#" class="flex flex-col space-y-8">
                  <div>
                    <h3 class="text-2xl">Your profile information</h3>
                    <hr />
                  </div>
                  <div>
                    <label class="text-xl">Full Name</label>
                    <input
                      type="text"
                      placeholder="Matvej Baranov"
                      class="w-full py-1 px-2 bg-blue-100"
                      disabled
                      v-model="User.userReqName"
                      ref='user'
                    />
                  </div>
                  <div class="flex flex-col space-y-4 md:space-y-0 md:flex-row md:space-x-4">
                    <div class="w-full">
                      <label class="text-xl">Username</label>
                      <input
                        type="text"
                        placeholder="DuckDivision"
                        class="w-full py-1 px-2 bg-blue-100"
                        disabled
                        v-model="User.userReqName"
                      />
                    </div>
                    <div class="w-full">
                      <label class="text-xl">Email</label>
                      <input
                        type="text"
                        placeholder="baranov-matvej@mail.ru"
                        class="w-full py-1 px-2 bg-blue-100"
                        disabled
                      />
                    </div>
                  </div>
                  <div>
                    <h3 class="text-2xl">More  About Me</h3>
                    <hr />
                  </div>
                  <div class="w-full">
                    
                    <label class="text-xl">Biography</label>
                    <textarea cols="30" rows="10" class="w-full py-1 px-2 bg-blue-100" disabled>
Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorem natus nobis odio. Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium, eveniet fugiat? Explicabo assumenda dignissimos quisquam perspiciatis corporis sint commodi cumque rem tempora!</textarea>
                  </div>
                  <div>
                    <h3 class="text-2xl">My Social Media</h3>
                    <hr />
                  </div>
                  <div>
                    <label class="text-xl">Instagram</label>
                    <input
                      type="text"
                      value="https://instagram.com/"
                      class="w-full py-1 px-2 bg-blue-100"
                      disabled
                    />
                  </div>
                  <div>
                    <label class="text-xl">Facebook</label>
                    <input
                      type="text"
                      value="https://facebook.com/"
                      class="w-full py-1 px-2 bg-blue-100"
                      disabled
                    />
                  </div>
                  <div>
                    <label class="text-xl">Twitter</label>
                    <input
                      type="text"
                      value="https://twitter.com/"
                      class="w-full py-1 px-2 bg-blue-100"
                      disabled
                    />
                  </div>
                </form>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
    <tbody>
        <tr v-for="user_ in User" :key="user_.gameResTitle">
          <td class="text-left"> {{ user_.gameResTitle}}</td>
          
        </tr>
      </tbody>
  </div>
  
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      User: []
    };
  },
  mounted() {
    axios.get("http://localhost:8081/stoom/game/all").then(responce => {
      console.log(responce.data);
      this.User = responce.data;
      this.$refs.user.placeholder = sessionStorage.getItem('user')
    });
  }
};
</script>

