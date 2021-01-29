<template>
  <div class="library">
    <div>
      <main>
        <div class="py-10 px-20">
          <table class="table-fixed">
            <thead>
              <tr>
                <th class="w-1/2 px-4 py-2">Image</th>
                <th class="w-1/4 px-4 py-2">Title</th>
                <th class="w-1/4 px-4 py-2">Play</th>
              </tr>
            </thead>
            <tbody ref="library">
              <!--
                        <tr>
                            <td class="border px-4 py-2">DOTA 2</td>
                            <td class="border px-4 py-2">Lorem ipsum dolor sit amet consectetur adipisicing elit.
                                Voluptates
                                earum odio repellat atque expedita ut incidunt mollitia! Placeat quidem, et, veniam
                                nostrum
                                perspiciatis aliquid facilis sunt sequi nemo commodi accusantium?</td>
                            <td class="border px-4 py-2">858</td>
                            <td class="border px-4 py-2">
                                <button
                                    class="bg-red-500 text-white font-bold py-4 px-2 rounded-full w-32 hover:bg-red-700">Play</button>
                            </td>
                        </tr>
                        <tr class="bg-gray-100">
                            <td class="border px-4 py-2">CS:GO</td>
                            <td class="border px-4 py-2">Lorem ipsum dolor sit amet consectetur adipisicing elit. Ad,
                                eum
                                adipisci placeat facilis possimus voluptas iure delectus. Animi odit cumque fugit
                                facilis
                                deserunt, non laborum qui, in aliquam excepturi cum.</td>
                            <td class="border px-4 py-2">112</td>
                            <td class="border px-4 py-2">
                                <button
                                    class="bg-red-500 text-white font-bold py-4 px-2 rounded-full w-32 hover:bg-red-700">Download</button>
                            </td>
                        </tr>
                        <tr>
                            <td class="border px-4 py-2">Hearthstone</td>
                            <td class="border px-4 py-2">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quod
                                quae
                                nam minus sint perspiciatis provident ducimus officiis similique veniam id delectus quis
                                exercitationem laudantium officia nostrum, tempore ipsum placeat eius.</td>
                            <td class="border px-4 py-2">1280</td>
                            <td class="border px-4 py-2">
                                <button
                                    class="bg-red-500 text-white font-bold py-4 px-2 rounded-full w-32 hover:bg-red-700">Download</button>
                            </td>
                        </tr>
-->
                <tr v-for="game in lib" v-bind:key="game.gameResID">
                    <td class="border px-4 py-2"><img style="height:200px;width:500px;object-fit: cover;" v-bind:src="game.gameResURL"></td>
                    <td class="border px-4 py-2">{{game.gameResTitle}}</td>
                    <td class="border px-4 py-2" style="text-align: center;">
                        <button
                            class="bg-red-500 text-white font-bold py-4 px-2 rounded-full w-32 hover:bg-red-700" v-on:click="downloadGame">Download
                        </button>
                    </td>
                </tr>
            </tbody>
          </table>
        </div>
      </main>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            lib: undefined
        };
    },
    mounted(){
        axios.get("http://localhost:8081/stoom/user/", {
            params : {
                userName: sessionStorage.getItem("user")
            },
            headers: {
                authorization: sessionStorage.getItem("authorization")
            }
        })
        .then(response => {
            let userKey = response.data[0].userResID;
            axios.get("http://localhost:8081/stoom/game_user/", {
                params : {
                    userID: userKey
                },
                headers: {
                    authorization: sessionStorage.getItem("authorization")
                }
            })
            .then(response => {
                this.lib = response.data;
            });
        });
    },
    methods: {
        downloadGame: function(event) {
            let gameCard = event.target.parentElement.parentElement;
            let url = gameCard.querySelector('img').src;
            console.log(url);
            let dummyLink = document.createElement("a");
            dummyLink.href = '';
            dummyLink.download = url;
            console.log(url);
            document.body.appendChild(dummyLink);
            dummyLink.click();
            console.log(dummyLink);
            document.body.removeChild(dummyLink);
        }
    }
}
</script>