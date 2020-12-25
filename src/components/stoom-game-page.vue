<template>
  <div id="gamePage">
    <div class="px-5 py-24 mx-auto">
      <div class="lg:w-3/5 mx-auto flex flex-wrap">
        <img
          alt="gameImage"
          class="lg:w-1/2 w-full object-cover object-center rounded border border-gray-200"
          src=""
          ref="img"
        />
        <div class="lg:w-1/2 w-full lg:pl-10 lg:py-6 mt-6 lg:mt-0">
          <h2 class="text-sm tracking-widest">BRAND NAME</h2>
          <h1 class="text-gray-900 text-3xl mb-1" ref="game_name">jfkrhgjk</h1>
          <div class="flex mb-4">
            <span class="flex items-center">
              <svg
                fill="currentColor"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                class="w-4 h-4 text-red-500"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
                />
              </svg>
              <svg
                fill="currentColor"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                class="w-4 h-4 text-red-500"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
                />
              </svg>
              <svg
                fill="currentColor"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                class="w-4 h-4 text-red-500"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
                />
              </svg>
              <svg
                fill="currentColor"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                class="w-4 h-4 text-red-500"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
                />
              </svg>
              <svg
                fill="none"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                class="w-4 h-4 text-red-500"
                viewBox="0 0 24 24"
              >
                <path
                  d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"
                />
              </svg>
              <span class="ml-3">4 Reviews</span>
            </span>
          </div>
          <p class="leading-relaxed">good game</p>
          <div class="flex py-8">
            <span class="title-font font-medium text-2xl" ref="price">$69.99</span>
            <button
              class="flex ml-auto buttonBuy items-center justify-center hover:bg-red-700"
              @click="buyGame"
            >Buy</button>
            
          </div>
        </div>
      </div>
    </div>

    <header class="text-center font-mono text-3xl py-8">
      <h3>Write your own review!</h3>
    </header>

    <div class="w-3/4 mx-auto">
      <div class="flex gap-5">
        <label class="text-xl">Rate it:</label>
        <input type="text" class="w-16 py-1 px-2 bg-red-200" v-model="Game.gameRate" />
      </div>
      <textarea cols="30" rows="10" class="w-full py-1 px-2 bg-gray-300" v-model="Game.gameReview">
          write smth
          </textarea>
    </div>

    <div class="flex justify-center">
      <button
        class="w-3/4 bg-yellow-400 px-2 py-1"
        type="submit"
        @click="addToReviewUser"
      >Submitt review</button>
    </div>

    

    
  </div>
</template>

<script>
import axios from "axios";
var gameName = sessionStorage.getItem("game_name");
//var userName = sessionStorage.getItem('user');
var userID;

export default {
  name: "stoom-game-page",
  props: {},
  data() {
    return {
      Game: { gameRate: "", gameReview: "" }
    };
  },
  methods: {
    addToReviewUser: function() {
      let Game = {
        gameRate: this.Game.gameRate,
        gameReview: this.Game.gameReview
      };

      let Review = {
        reviewAssessment: Game.gameRate,
        reviewGameID: sessionStorage.getItem("game_id"),
        reviewText: Game.gameReview,
        reviewUserID: userID
      };
      console.log(Game);
      axios
        .post("http://localhost:8081/stoom/review/", Review, {
          headers: {
            authorization: sessionStorage.getItem("authorization")
          }
        })
        .then(response => {
          console.log(response);
        });
    },
    buyGame: function() {
      //console.log("hello");
      let bGame = {
        reviewGameID: sessionStorage.getItem("game_id"),
        reviewUserID: userID
      };
      axios
        .post("http://localhost:8081/stoom/game_user/", bGame, {
          headers: {
            authorization: sessionStorage.getItem("authorization")
          }
        })
        .then(response => {
          console.log(response);
        });
    }
  },
  mounted() {
    axios
      .get(
        "http://localhost:8081/stoom/game/getGameByTitle?gameTitle=" + gameName,
        {}
      )
      .then(response => {
        axios
          .get("http://localhost:8081/stoom/user/getUserID", {
            params: {
              userName: sessionStorage.getItem("user")
            },
            headers: {
              authorization: sessionStorage.getItem("authorization")
            }
          })
          .then(responce => {
            userID = responce;
            console.log(userID);
            console.log(responce);
            userID = responce.data.userResID;
          });
        console.log(response.data);
        this.User = response.data[0];
        sessionStorage.setItem("price", response.data[0].gameResPrice);
        sessionStorage.setItem("game_id", response.data[0].gameResID);
        //sessionStorage.setItem('img', response.data[0].gameResURL)
        this.$refs.game_name.innerHTML = sessionStorage.getItem("game_name");
        this.$refs.price.innerHTML = sessionStorage.getItem("price");
        this.$refs.img.src = response.data[0].gameResURL;
        console.log(response);
      });
  }
};
</script>