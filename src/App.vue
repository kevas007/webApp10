<template>
<AppHeader/>
  <div class="m-5 flex flex-col" >
    <h1 class="text-4xl text-center">Heros</h1>
    <ul class="w-4/12 mx-auto">
      <li v-for="(hero, index) in dcHeros" :key="index">
      <div class="flex justify-between m-5"> 
        {{ index + 1 }} - {{ hero.name }} 
        <button  @click="removeHeros(index)" class="px-3 py-1 font-medium tracking-wide text-white capitalize transition-colors duration-200 transform bg-red-600 rounded-md dark:bg-gray-800 hover:bg-red-500 dark:hover:bg-gray-700 focus:outline-none focus:bg-red-500 dark:focus:bg-gray-700">
          X
          </button> 
        </div>
      </li>
    </ul>
      <form   class="flex w-4/12 mx-auto justify-between " 
        @submit.prevent="addHeros"
        > 
        <input v-model="newHero" placeholder="Type Hero name" type="text" class="block w-50 px-4 ml-5 py-2 mt-2  text-gray-700 bg-white border border-gray-300 rounded-md dark:bg-gray-800 dark:text-gray-300 dark:border-gray-600 focus:border-blue-500 dark:focus:border-blue-500 focus:outline-none focus:ring">
      <button type="submit" class="px-6 py-2 leading-5  mt-2 text-white transition-colors duration-200 transform bg-gray-700 rounded-md hover:bg-gray-600 focus:outline-none focus:bg-gray-600">Add Heros</button>
    </form>

  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
export default {
components: {
  AppHeader
},
  methods: {
    addHeros(){
      if(this.newHero !==''){
      this.dcHeros.push({ name:this.newHero });
      this.newHero = '';  // reset the input
      }
      
    },
    removeHeros(index){
      this.dcHeros= this.dcHeros.filter((hero, i)=> i !== index);
    }
  },
  
  data() {
    return {
      newHero: '',
      dcHeros: [
        { name: "SuperMan" },
        { name: "Batman" },
        { name: "SpiderMan" },
        { name: "IronMan" },
        { name: "Hulk" },
        { name: "Thor" }
      ],
    };
  },
}
</script>
