<template>
<the-header title="RememberMe"></the-header>
   <stored-resource :resources="storedResources"></stored-resource>
</template>

<script>  
import storedResource from './components/Resource/StoredResource.vue';
import TheHeader from './components/layouts/TheHeader.vue'


export default {
  name: 'App',
  components:{
     storedResource,TheHeader
  },
  data(){
    return { 
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
    }
  }
   
}
</script>


<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100&display=swap');

* {
  box-sizing: border-box;
}
html {
  font-family: 'Roboto',sans-serif;
}

body {
  margin:0;
}
</style>