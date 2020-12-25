<template>
  <div class="library">
    <div> 
      <main>
         <div class="py-10 px-20">
                <table class="table-fixed">
                    <thead>
                        <tr>
                            <th class="w-1/2 px-4 py-2">Title</th>
                            <th class="w-1/4 px-4 py-2">Lorem</th>
                            <th class="w-1/4 px-4 py-2">Hours</th>
                            <th class="w-1/4 px-4 py-2">Play</th>
                        </tr>
                    </thead>
                    <tbody
                    ref="library"
                    >
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
            gameRow: `
                <td class="border px-4 py-2 name"></td>
                <td class="border px-4 py-2">
                    <button
                        class="bg-red-500 text-white font-bold py-4 px-2 rounded-full w-32 hover:bg-red-700">Download</button>
                </td>
            `
        }
    },
    mounted(){
        axios.get("http://localhost:8081/stoom/game/all", /*{
                params: {
                    userID: '24979136-39eb-4b09-acd7-a0765cc7f90f',
                },
                headers: {
                    authorization: sessionStorage.getItem("authorization"),
                },
            },
           ,*/
            (response) => {
                console.log(response)
                for(var i = 0; i < response.length; i++) {
                    var game = document.createElement('tr')
                    game.classList.add("bg-gray-100")
                    game.innerHTML = this.$data.gameRow
                    game.querySelector('td.name').innerHTML = response[i].gameResTitle;
                    this.$refs.library.appendChild(game);
                }
        })
    }
}
</script>