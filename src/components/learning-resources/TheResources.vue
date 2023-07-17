<template>
    <base-card>
    <div class="btn-container">
        <base-button @click="setTab('stored-resources')" :mode="selectedTab === 'stored-resources' ? null : 'flat'" >Stored Resources</base-button>
        <base-button @click="setTab('add-resources')" :mode="selectedTab === 'stored-resources' ? 'flat' : null " >Add Resources</base-button>
    </div>    
    
    </base-card>
    <component :is="selectedTab"></component>
</template>



<script>
import StoredResources from './StoredResources.vue'
import AddResources from './AddResources.vue';
export default{
    emits:['set-tab','emit-resource'],
    components:{StoredResources,AddResources},
    provide(){
        return {resources:this.storedResources,
        addresource:this.addResource,
        deleteresource:this.deleteResource}
    },
    data() {
        return {
            selectedTab:'stored-resources',
            storedResources:[
        {id:'official-guide',tittle:'Official Guide',description:'The official Vue.js documentation.',link:'https://vuejs.org'},
      {id:'google',tittle:'Google',description:'Go to Google.',link:'https://google.org'}
    ],
        }
    },

    methods: {
        setTab(tab){
            this.selectedTab = tab;
        },
        addResource(tittle,description,link){
        const item = {id:tittle,tittle:tittle,description:description,link:link}
            this.storedResources.push(item)
        },
        deleteResource(id){
            const idx = this.storedResources.findIndex(res => res.id === id)
            console.log(idx)
            this.storedResources.splice(idx,1)
            
        }

    },
};
</script>

<style scoped>
    .btn-container{
        display: flex;
        justify-content: center;
        
    }
</style>