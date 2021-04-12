<template>
    <div class="mt-10 ml-10">
        <div class="flex mb-5 mt-1 justify-between">
        <nav class="flex" aria-label="Breadcrumb">
            <ol class="flex items-center space-x-4">
            <li>
            <div>
                <a href="#" class="text-gray-400 hover:text-gray-500">
                <!-- Heroicon name: home -->
                <svg class="flex-shrink-0 h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                    <path d="M10.707 2.293a1 1 0 00-1.414 0l-7 7a1 1 0 001.414 1.414L4 10.414V17a1 1 0 001 1h2a1 1 0 001-1v-2a1 1 0 011-1h2a1 1 0 011 1v2a1 1 0 001 1h2a1 1 0 001-1v-6.586l.293.293a1 1 0 001.414-1.414l-7-7z" />
                </svg>
                <span class="sr-only">Inicio</span>
                </a>
            </div>
            </li>
            <li>
            <div class="flex items-center">
                <!-- Heroicon name: chevron-right -->
                <svg class="flex-shrink-0 h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" aria-hidden="true">
                <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
                </svg>
                <a href="#" class="ml-4 text-sm font-medium text-gray-500 hover:text-gray-700">Empresas</a>
            </div>
            </li>            
        </ol>
        </nav>                
    </div>
         <div class="flex flex-col mt-20 mx-10">
            <div class="my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
                <div class="py-2 align-middle inline-block min-w-full sm:px-6 lg:px-8">
                    <div class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg text-center">              
                       <!--  <table class="min-w-full divide-y divide-gray-200">
                            <thead class="bg-blue-100">
                                <tr>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-700 uppercase tracking-wider">
                                    id
                                    </th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-700 uppercase tracking-wider">
                                    name
                                    </th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-700 uppercase tracking-wider">
                                    email
                                    </th>
                                    <th scope="col" class="px-6 py-3 text-left text-xs font-bold text-gray-700 uppercase tracking-wider">
                                    Opciones
                                    </th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr class="bg-white hover:bg-gray-200 cursor-pointer" v-for="item in results"
                                    :key="item.id">
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500" @click="showUser(item.id)">
                                   <nuxt-link :to="{ path: '/Users/Show' , query: { userId: item.id }}"> {{item.id}}</nuxt-link>
                                    </td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500" @click="showUser(item.id)">
                                    {{item.name}}
                                    </td>
                                    <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500" @click="showUser(item.id)">
                                    {{item.email}}
                                    </td>                                                  
                                    <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">                          
                                        <div class="flex z-40">
                                        </div>
                                    </td>
                                </tr>
                            </tbody>
                        </table> -->
                         <div class="flex flex-col mx-10 my-10" style="background-color:#680F19"> 
                             <div class="w-full mx-auto my-20 text-white text-6xl">
                                 ORBITWEB TV.
                                 
                            </div>                            
                              <div class="w-full ml-40 mb-10">
                                  <v-clappr 
                                    el="player"
                                    source="https://cdn.elsalvadordigital.com:1936/wowtv/smil:wowtv.smil/playlist.m3u8"
                                    :options="options"
                                    @init="oninit"
                                    @ready="onready"
                                    @play="onplay"
                                    @pause="onpause"
                                    @stop="onstop"
                                    @ended="onended"
                                    @fullscreen="onfullscreen"
                                    @resize="onresize"
                                    @seek="onseek"
                                    @timeupdate="ontimeupdate"
                                    @volumeupdate="onvolumeupdate"
                                    @error="onerror"
                                />
                              </div>
                         </div>
                    </div>
                </div>
            </div>
        </div> 
    </div>
</template>
<script>
import VClappr from 'v-clappr'
export default {
    data(){
        return{
          results : [],
        }
    },
    mounted() {
        this.fetchSomething()
        console.log('requesting data')
    },
    components:{
       VClappr
    },
    methods:
    {
      async fetchSomething() {
        const ip = await this.$axios.$get('http://127.0.0.1:8000/api/users')
        this.results = ip     
      },
      showUser(id){
        console.log(id)
      }
    },
}
</script>