<template>
   <base-card v-for="target in targets" :key="target.id"> 
  
      {{target.campaign}} || {{target.type}}

    <button @click="deleteTarget(target.id)" type="button">Delete</button>
   </base-card>
</template>


<script>

export default {
   emits:["deletetarget"],
   inject: ["targets"],
   methods:{
       deleteTarget(id){
           this.$emit("deletetarget",id);
       }
   }
}
</script>