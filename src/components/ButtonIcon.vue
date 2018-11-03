<template>
    <div>
         <button type="button" class="btn btn-info" @click="sendtext">
              <span :class="icon"></span> {{name}} 
         </button>
    </div>
</template>

<script>
export default {
 props: {
     icon: {
         type: String,
         default: 'fa fa-search' 
     },
     name: {
         type: String,
         default: 'Click Me' 
     },
 },methods: {
     sendtext() {
         this.$emit('buttontext',20)
     }
 },
}
</script>

<style scoped>
</style>