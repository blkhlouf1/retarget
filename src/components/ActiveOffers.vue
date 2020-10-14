<template>
<base-card>
<label for="sponsor"> Select Network </label>
        <select id="sponsor" name="sponsor" @input="selectSponsor" ref="selectedSponsor">
            <option v-for="sponsor in allSponsors"  :value=sponsor :key=sponsor >{{ sponsor }}</option>
        </select>
        <label for="offer"> Select offer </label>
        <select id="offer" name="offer"  @input="selectOffer"  ref="selectedOffer">
            <option v-for="offer in allOffers"  :value=offer :key=offer>{{ offer }}</option>
        </select>
</base-card>
</template>


<script>
export default {
    emits:["selectsponsor","selectoffer"],
   data(){
       return{
            allSponsors: ["W4","Trax","mint"],
            allOffers: ["exemple1","exemple2","exemple3"],

       };
   },
   methods:{
       selectSponsor(){
           const sponsor  =  this.$refs.selectedSponsor.value;
           this.$emit("selectsponsor",sponsor);
       },
       selectOffer(){
           const offer = this.$refs.selectedOffer.value;
           this.$emit("selectoffer",offer);
       }
       
   }
}
</script>