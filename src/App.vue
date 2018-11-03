<template>
  <div id="app">    
     <navbar></navbar>
    <button class="btn btn-sucsess"  @click="isNew =!isNew ">Create</button>
    <RecipesForm @Saverecipe="addRecipe" v-if="isNew" ></RecipesForm>
    <input type="text" class="form-control" v-model="searchtext" >
    <ul>
      <li v-for="(recipe,index) in filterListtest" :key="index+recipe.title">
            {{recipe.title}}
            
      </li>
    </ul>
  </div>
</template>

<script>
import navbar from './layout/navbar.vue'
import RecipesForm from './components/RecipesForm.vue'

export default {
  name: 'app',
  components: {
    navbar,
    RecipesForm
  },methods: {
    searchLocalStorage(){
       localStorage.setItem('recipe',JSON.stringify(this.recipes))
    },
    addRecipe(recipe) {      
      this.recipes.push(recipe)     
      this.searchLocalStorage()
      this.isNew = false
    },
    searchRecipe() {    
      this.recipes = this.recipes.filter((recipe) => {
        return recipe.title.toLowerCase().indexOf(this.searchtext.toLowerCase()) > - 1
      })      
    }
  },data() {
    return {
      recipes: [],
      isNew:false,
      searchtext:''
    }
  },mounted() {
     if(localStorage.getItem('recipes'))
     {
        this.recipes = JSON.parse(localStorage.getItem('recipes'))
     }
  },computed: {
     filterListtest() {
      return this.recipes.filter((recipe) => {
        return recipe.title.toLowerCase().indexOf(this.searchtext.toLowerCase()) > - 1
      })       
    }
  },
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style>
