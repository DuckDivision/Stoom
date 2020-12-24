<template>
  <div id="profileInformation">
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
              value="Matvej Baranov"
              class="w-full py-1 px-2 bg-blue-100"
              disabled
              ref='user'
            />
          </div>
          <div
            class="flex flex-col space-y-4 md:space-y-0 md:flex-row md:space-x-4"
          >
            <div class="w-full">
              <label class="text-xl">Username</label>
              <input
                type="text"
                value="DuckDivision"
                class="w-full py-1 px-2 bg-blue-100"
                disabled
                
              />
            </div>
            <div class="w-full">
              <label class="text-xl">Email</label>
              <input
                type="text"
                value="baranov-matvej@mail.ru"
                class="w-full py-1 px-2 bg-blue-100"
                disabled
              />
            </div>
          </div>
          <div>
            <h3 class="text-2xl">More About Me</h3>
            <hr />
          </div>
          <div class="w-full">
            <label class="text-xl">Biography</label>
            <textarea
              cols="30"
              rows="10"
              class="w-full py-1 px-2 bg-blue-100"
              disabled
            >
Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorem natus nobis odio. Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium, eveniet fugiat? Explicabo assumenda dignissimos quisquam perspiciatis corporis sint commodi cumque rem tempora!</textarea
            >
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
    axios
      .get("http://localhost:8081/stoom/user/", {
        params: {
          userName: sessionStorage.getItem("user")
        },
        headers: {
          authorization: sessionStorage.getItem("authorization")
        }
      })
      .then(response => {
        console.log(response.data);
        this.User = response.data;
        this.$refs.user.value = sessionStorage.getItem('user');
      });
  }
};
</script>