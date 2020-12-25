<template>
  <div class="home">
    <header class="text-center font-mono text-3xl py-8">
      <h2>Welcome, to STOOM</h2>
    </header>

    <div class="mx-20">
      <h4 class="mx-20 text-xl">Latest games</h4>

      <div>
        <!-- cards go here -->
        <div class="grid xl:grid-cols-5 md:grid-cols-3 sm:grid-cols-1 gap-10 text-left py-5">
          <div class="shadow-xl">
            <img
              src="https://assets1.ignimgs.com/2019/05/31/mario-64---button-1559263987447.jpg"
              alt="SuperMario64"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">The Witcher 3 Wild Hunt</span>
              <span class="text-right pr-2">1999р</span>
              <span class="text-sm">Game by Nintendo</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
          <div class="shadow-xl">
            <img
              src="https://nowcdkey.com/wp-content/uploads/2019/07/cover-nowcdkey2019-44.jpg"
              alt="RocketLeague"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Call Of Duty Modern Warfare</span>
              <span class="text-right pr-2">FREE</span>
              <span class="text-sm">Game by Psyonix</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
          <div class="shadow-xl">
            <img
              src="https://games-conventions.ru/Frontend/images/convent_logos/year_2018/tavern-of-heroes-turnir-po-starcraft-2-13-01-2018-logo.jpg"
              alt="Starcraft2"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Call Of Duty Cold War</span>
              <span class="text-right pr-2">499р</span>
              <span class="text-sm">Game by Blizzard</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
          <div class="shadow-xl">
            <img
              src="https://img.championat.com/c/1200x900/news/big/y/s/prodazhi-minecraft-dostigli-otmetki-v-200-mln-kopij_1589836261263264197.jpg"
              alt="Mineraft"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Divinity Original Sin 2 Definitive Edition</span>
              <span class="text-right pr-2">1499р</span>
              <span class="text-sm">Game by Microsoft</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
          <div class="shadow-xl">
            <img
              src="https://www.mobygames.com/images/covers/l/380359-for-honor-playstation-4-front-cover.png"
              alt="ForHonor"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Far Cry 5 Gold Edition</span>
              <span class="text-right pr-2">299р</span>
              <span class="text-sm">Game by Ubisoft</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
        </div>
      </div>

      <h4 class="mx-20 text-xl">Most Popular</h4>

      <div>
        <!-- cards go here -->
        <div class="grid xl:grid-cols-5 md:grid-cols-3 sm:grid-cols-1 gap-10 text-left py-5">
          <div class="shadow-xl">
            <img
              src="https://assets1.ignimgs.com/2019/05/31/mario-64---button-1559263987447.jpg"
              alt="SuperMario64"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Far Cry 5 Gold Edition</span>
              <span class="text-right pr-2">1999р</span>
              <span class="text-sm">Game by Nintendo</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
          <div class="shadow-xl">
            <img
              src="https://nowcdkey.com/wp-content/uploads/2019/07/cover-nowcdkey2019-44.jpg"
              alt="RocketLeague"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Far Cry 5 Gold Edition</span>
              <span class="text-right pr-2">FREE</span>
              <span class="text-sm">Game by Psyonix</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
          <div class="shadow-xl">
            <img
              src="https://games-conventions.ru/Frontend/images/convent_logos/year_2018/tavern-of-heroes-turnir-po-starcraft-2-13-01-2018-logo.jpg"
              alt="Starcraft2"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Far Cry 5 Gold Edition</span>
              <span class="text-right pr-2">499р</span>
              <span class="text-sm">Game by Blizzard</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button class="buttonBuy hover:bg-red-700"
                v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
          <div class="shadow-xl">
            <img
              src="https://img.championat.com/c/1200x900/news/big/y/s/prodazhi-minecraft-dostigli-otmetki-v-200-mln-kopij_1589836261263264197.jpg"
              alt="Mineraft"
              class="object-cover h-56 w-full"
            />
            <div class="grid grid-cols-2 px-2 py-2">
              <span class="text-lg">Far Cry 5 Gold Edition</span>
              <span class="text-right pr-2">1499р</span>
              <span class="text-sm">Game by Microsoft</span>
              <router-link to="/gamePage" class="flex flex-row-reverse">
                <button
                  class="buttonBuy hover:bg-red-700"
                  v-on:click="getGame"
                >Buy</button>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div>
      <div class="py-10 text-center">
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. Itaque alias,
        enim repudiandae asperiores voluptas incidunt libero molestias esse illo
        dolores fugiat corrupti! Quam, rem voluptates! Sed eius a aliquid
        commodi.
      </div>
    </div>
  </div>
</template>

<script>
//import axios from "axios";
export default {
  name: "Home",
  data() {
    return {};
  },
  methods: {
    getGame: function(e){
      var clickedElement = e.target;
      console.log(clickedElement)
      var addGameName = clickedElement.parentElement.parentElement.querySelector("span.text-lg").innerHTML;
      console.log(addGameName)
      sessionStorage.setItem("game_name", addGameName);
      //this.$router.push({ name: '#/gamePage' })
      //this.$refs.game_name.innerHTML = addGameName;
    }
  },
    
  
};
</script>
