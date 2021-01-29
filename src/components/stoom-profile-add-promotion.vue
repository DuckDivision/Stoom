<template>
  <div id="profilePromoteGame">
    <div
      class="col-span-12 md:border-solid md:border-l md:border-black md:border-opacity-25 h-full pb-12 md:col-span-10"
    >
      <div class="px-4 pt-4">
        <form action="#" class="flex flex-col space-y-8">
          <div>
            <h3 class="text-2xl">Promote your crap!</h3>
            <hr />
          </div>
          <div>
            <label class="text-xl">Name of the game</label>
            <select class="w-full py-1 px-2 bg-green-300"
            v-model="PromoAdd.namePromo"
            >
              <option>Far Cry 5 Gold Edition</option>
              <option>3</option>
              <option>5</option>
            </select>
          </div>
          <div class="w-full">
            <label class="text-xl">Sale %</label>
            <input type="text" class="w-full py-1 px-2 bg-green-300" 
            v-model="PromoAdd.sale"
            />
          </div>
          <div class="w-full">
            <label class="text-xl">URL</label>
            <input type="text" class="w-full py-1 px-2 bg-green-300" 
            v-model="PromoAdd.URLPromo"
            />
          </div>
          <div>
            <h3 class="text-2xl">Discount description</h3>
            <hr />
          </div>
          <div class="w-full">
            <textarea
              cols="30"
              rows="10"
              class="w-full py-1 px-2 bg-green-300"
              disabled
            >
Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolorem natus nobis odio. Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium, eveniet fugiat? Explicabo assumenda dignissimos quisquam perspiciatis corporis sint commodi cumque rem tempora!</textarea
            >
          </div>
          <div class="pt-4 flex justify-center">
            <button class="w-64 bg-green-400 px-2 py-1" type="submit"
            @click="AddPromo"
            >
              Start promotion
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
      PromoAdd: {  }
    };
  },

  methods: {
    AddPromo() {
      let PromoAdd = {
        gameReqPrice: this.PromoAdd.sale,
        gameReqTitle: this.PromoAdd.namePromo,
        gameReqURL: this.PromoAdd.URLPromo
        
      };
      console.log(PromoAdd);
      axios
        .put("http://localhost:8081/stoom/game/", PromoAdd,
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