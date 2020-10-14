<template>
<base-card>
    <label for="campaign"> Campaign </label>
        <select id="campaign" name="campaign" ref="selectedCampaign">
            <option v-for="campaign in campaigns"  :value=campaign :key=campaign>{{ campaign }}</option>
        </select>
    <label for="Type"> Type </label>
        <select id="type" name="type" ref="selectedType">
            <option value="openers">Openers</option>
            <option value="clickers">Clicker</option>
        </select>
        <button @click="sendTarget()" type="button">Add Target</button>
</base-card>
</template>


<script>
export default {
    emits:["sendtarget"],
    data(){
        return{
             campaigns: ["1233","23443","33344"]
        }
    },
    methods:{
        sendTarget(){
             const campaign =  this.$refs.selectedCampaign.value;
             const type =  this.$refs.selectedType.value;
             this.$emit("sendtarget",campaign, type);
            }
        }
    
    
}
</script>