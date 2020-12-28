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
              <button

                class="text-sm p-2 text-center bg-yellow-500"
                type="button"
                @click="displayInformation"

              >
                Information
              </button>
              <button


                  v-if="isAdmin()"
                  class="text-sm p-2 text-center bg-yellow-500"
                  type="button"
                  @click="displayGame"


              >
                Add new game
              </button>
              <button

                v-if="isAdmin()"
                class="text-sm p-2 text-center bg-yellow-500"
                type="button"
                @click="displayPromotion"


              >
                Promotion
              </button>
            </div>
            <div
                class="col-span-12 md:border-solid md:border-l md:border-black md:border-opacity-25 h-full pb-12 md:col-span-10"
            >
              <stoom-profile-information v-show="isInformationVisible" />
              <stoom-profile-add-game v-show="isGameVisible" />
              <stoom-profile-add-promotion v-show="isPromotionVisible" />
            </div>
          </div>
        </div>
      </main>
    </div>
    <tbody>
    <tr v-for="user_ in User" :key="user_.gameResTitle">
      <td class="text-left">{{ user_.gameResTitle }}</td>
    </tr>
    </tbody>
  </div>
</template>

<script>
import stoomProfileInformation from '../components/stoom-profile-information.vue';
import stoomProfileAddGame from "../components/stoom-profile-add-game";
import stoomProfileAddPromotion from "../components/stoom-profile-add-promotion";
import axios from "axios";
export default {
  name: "profile",
  components: {
    stoomProfileInformation,
    stoomProfileAddGame,
    stoomProfileAddPromotion
  },
  data() {
    return {
      User: [],
      isInformationVisible: false,
      isGameVisible: false,
      isPromotionVisible: false,
<<<<<<< HEAD

=======
>>>>>>> night
    };
  },
  methods: {
    displayInformation() {
      this.$data.isInformationVisible = true;
<<<<<<< HEAD

=======
>>>>>>> night
      this.$data.isGameVisible = false;
      this.$data.isPromotionVisible = false;
    },
    displayGame() {
      this.$data.isInformationVisible = false;
<<<<<<< HEAD

=======
>>>>>>> night
      this.$data.isGameVisible = true;
      this.$data.isPromotionVisible = false;
    },
    displayPromotion() {
      this.$data.isInformationVisible = false;
<<<<<<< HEAD

=======
>>>>>>> night
      this.$data.isGameVisible = false;
      this.$data.isPromotionVisible = true;
    },
    isAdmin() {
      return sessionStorage.getItem('role') == 'ROLE_ADMIN';
    }
<<<<<<< HEAD

=======
>>>>>>> night
  },
  mounted() {
    axios
        .get("http://localhost:8081/stoom/user/", {
          params: {
            userName: sessionStorage.getItem("user"),
          },
          headers: {
            authorization: sessionStorage.getItem("authorization"),
          },
        })
        .then((response) => {
          console.log(response.data);
          this.User = response.data;
        });
  },
};
<<<<<<< HEAD
</script>
=======
</script>
>>>>>>> night
