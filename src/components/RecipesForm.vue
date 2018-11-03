
<template>
    <div>
      <form @submit.prevent="" class="form-horizontal">
<fieldset>
<pre>
                    {{ recipe}}
                </pre>
               
<!-- Form Name -->
<legend>Recipe Form</legend>

<!-- Text input-->
<div class="form-group row">
  <label class="col-md-4 control-label" for="txtTitle">Title</label>  
  <div class="col-md-4">
  <input id="txtTitle" name="txtTitle" type="text" placeholder="Your Title" class="form-control input-md" v-model="recipe.title">
    
  </div>
</div>

<!-- Text input-->
<div class="form-group row">
  <label class="col-md-4 control-label" for="txtDescription">Description</label>  
  <div class="col-md-4">
  <input id="txtDescription" name="txtDescription" type="text" placeholder="Your Description" class="form-control input-md" v-model="recipe.description">
    
  </div>
</div>

<!-- Text input-->
<div class="form-group row">
  <label class="col-md-4 control-label" for="txtImage">Image</label>  
  <div class="col-md-4">
  <input id="txtImage" name="txtImage" type="text" placeholder="Your Image url"  v-model="recipe.image" class="form-control input-md">
    
  </div>
</div>
<div class="row">
    <div class="col">
        <button id="btnCancel" name="btnCancel" class="btn btn-defalut" @click="addingredient" >More Ingredients</button>
    </div> 
</div>
<!-- Text input-->
<div class="form-group row">
  <label class="col-md-4 control-label" for="txtIngredients">Ingredients</label>  
  <div class="col-md-4">
      <div  v-for="(ingredient,index) in recipe.ingredient" :key="index" >
           <input v-model="recipe.ingredient[index]"  name="txtIngredients" type="text" placeholder="Your Ingredients" class="form-control input-md">
    
      </div>
 
  </div>
</div>

<!-- Button (Double) -->
<div class="form-group">  
  <div class="col-md-12">
    <button id="btnCancel" name="btnCancel" class="btn btn-danger">Cancel</button>
    <button id="btnSave" name="btnSave" class="btn btn-success" @click="save" >Save</button>
  </div>
</div>

</fieldset>
</form>

    </div>
</template>

<script>
export default {
data() {
    return {
        recipe:{
            title: '',
            description:'',
            image:'',
            ingredient:['']
        }
    }
},methods: {
    addingredient() {
        this.recipe.ingredient.push('')
    },save(){
        this.$emit('Saverecipe',this.recipe)
    }
},
}
</script>

<style scoped>
</style>