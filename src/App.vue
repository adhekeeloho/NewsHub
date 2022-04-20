<template>
  <v-app id="inspire">

    <v-app-bar app 
    class="news"
    >
       <v-list-item-content align="start" justify="start">
          <v-list-item-title class="text-h6 white--text" style="font-family: 'Poppins', sans-serif; ">
            <v-icon x-large class="pr-2 float" color="white">mdi-newspaper-variant-multiple-outline</v-icon> 
            News Hub
          </v-list-item-title>
        </v-list-item-content>
      
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({ 
      drawer: null,
      items: [
      { title: "News",  to: "/" },
    ],
    }),
    
  }
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

.news{
  background: linear-gradient(to right, #005BBB  0%, #FFD500 100%);
}

.float {  
    animation-name: floating;
    animation-duration: 3s;
    animation-iteration-count: infinite;
    animation-timing-function: ease-in-out;
}

@keyframes floating {
    from { transform: translate(0,  0px); }
    65%  { transform: translate(0, 10px); }
    to   { transform: translate(0, -0px); }    
}
</style>