<template>
    <form @submit.prevent="submitRequest">
        <the-header title="Retargeting"></the-header>
        <active-offers @selectoffer="selectOffer" @selectsponsor="selectSponsor"></active-offers>
        <add-target @sendtarget="addTarget" ></add-target>
        <targets-holder @deletetarget="deleteTarget"></targets-holder>
        <base-button type="submit">Create</base-button> 
    </form>
    
 
</template>


<script>
import ActiveOffers from './components/ActiveOffers.vue';
import TargetsHolder from './components/TargetsHolder.vue';
import TheHeader from './UI/TheHeader.vue';
import AddTarget from './components/AddTarget.vue';


export default {
  components: {
        ActiveOffers,
        TargetsHolder,
        TheHeader,
        AddTarget
  },
    
    methods: {
        selectOffer(offer){
            this.selectedOffer = offer;

        },
        selectSponsor(sponsor){
            this.selectedSponsor = sponsor;
        },
        submitRequest(){
            console.log(JSON.stringify(this.$data));
        },
        addTarget(campaign, type){
            const newTarget = {
                id: new Date().toISOString(),
                campaign: campaign,
                type: type
            };
            this.allTargets.push(newTarget);
        },

        deleteTarget(id){
            const tarIndex = this.allTargets.findIndex(targ => targ.id === id);
            this.allTargets.splice(tarIndex, 1);
        }
      },
  

    provide(){
        return {
            targets: this.allTargets
        };
    },

    data(){
        return {
            selectedSponsor: 'trax',
            selectedOffer: '0019',
            allTargets: [{
                id:'jhsjkfdkf',
                campaign:'5454',
                type:'openers'
            }],
            
        };
    }
    
}
   
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}

</style>