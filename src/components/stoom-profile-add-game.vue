<template>
  <div id="profileAddGame">
    <div
      class="col-span-12 md:border-solid md:border-l md:border-black md:border-opacity-25 h-full pb-12 md:col-span-10"
    >
      <div class="px-4 pt-4">
        <form action="#" class="flex flex-col space-y-8">
          <div>
            <h3 class="text-2xl">Send your crap</h3>
            <hr />
          </div>
          <div>
            <label class="text-xl">Name of the game</label>
            <input type="text" class="w-full py-1 px-2 bg-red-200"
            v-model="GameAdd.nameGame"
             />
          </div>
          <div class="w-full">
            <label class="text-xl">Price</label>
            <input type="text" class="w-full py-1 px-2 bg-red-200"
            v-model="GameAdd.priceGame"
             />
          </div>
          
          <div class="w-full">
            <label class="text-xl">Game image</label>
            <input type="text" class="w-full py-1 px-2 bg-red-200" 
            v-model="GameAdd.URLGame"
            />
          </div>
          
          <div class="pt-4 flex justify-center">
            <button class="w-64 bg-red-300 px-2 py-1" type="submit"
            @click="AddGame"
            >
              SUBMITT THE GAME
            </button>
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
      GameAdd: {  }
    };
  },

  methods: {
    AddGame() {
      let GameAdd = {
        gameReqPrice: this.GameAdd.priceGame,
        gameReqTitle: this.GameAdd.nameGame,
        gameReqURL: this.GameAdd.URLGame
        
      };
      console.log(GameAdd);
      axios
        .post("http://localhost:8081/stoom/game/", GameAdd,
        {
          headers:{
            authorization: sessionStorage.getItem('authorization')
          }
        }
        )
        .then(response => {
          
          console.log(response);
        });
    }
  }
};
</script>