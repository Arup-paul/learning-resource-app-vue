<template>
    <base-card>
       <base-button @click="setSelectedTab('stored-resource')" :mode="storeResourceButtonMode">Stored Resources</base-button>
       <base-button @click="setSelectedTab('add-resource')" :mode="addResourceButtonMode">Add Resource </base-button>
    </base-card>
    <keep-alive>
     <component :is="selectedTab"></component>
    </keep-alive>
</template>


<script>
import storedResource from './StoredResource.vue';
import AddResource from './AddResource.vue'

 export default {
     components: {
         storedResource,AddResource
     },
     data() {
         return {
             selectedTab:'stored-resources',
              storedResources: [
        { 
          id: 1,
          title: 'Official Guide',
          description:'The Official Vue.js Documentation',
          link:'https://vuejs.org/'
        },
         { 
          id: 2,
          title: 'Vuex',
          description:'The Official Vuex Documentation',
          link:'https://vuex.vuejs.org/'
        }
      ],
         };
     },
     provide() {
         return {
             resources: this.storedResources,
             addResource: this.addResource
         }
     },
     computed: {
       storeResourceButtonMode(){
           return this.selectedTab === 'stored-resource' ? null : 'flat';
       },
       addResourceButtonMode(){
           return this.selectedTab === 'add-resource' ? null : 'flat';
       }
     },
     methods: {
         setSelectedTab(tab) {
             this.selectedTab = tab
         },
         addResource(title,description,url) {
           const newResource = {
               id: new Date().toISOString(),
               title:title,
               description:description,
               link:url
           };
           this.storedResources.unshift(newResource);
           this.selectedTab = 'stored-resource';

         }
     }
 }
</script>