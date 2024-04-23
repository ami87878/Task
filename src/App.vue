<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Task App
          </v-list-item-title>
          <v-list-item-subtitle>
            any task you should do
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
          :to="item.to"
          
        >
          <v-list-item-icon>
            <v-icon color="#2E7D32">{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    
    <v-app-bar
      app
   
      color="#26A69A"
      dark

      prominent
      src="../public/niagarafalls-from-the-air-1623267.jpg"
      fade-img-on-scroll
      
      scroll-threshold="500"
      height="150px"
    >
      <template v-slot:img="{ props }">
        <v-img
          
          v-bind="props"
          gradient="to top right, rgba(144,222,231,1),rgba(82,255,178,0.2) "
        ></v-img>
        
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title> Add Tasks🎯🎯</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon >mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
      
    </v-app-bar>



    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => (
      
    { 
      
      drawer: false,
      items: [
        { title: 'work', icon: 'mdi-book-cog-outline',to:'/'},
        
        { title: 'About', icon: 'mdi-information-variant', to:'/about' },
        ], 
    
    
    
    }),
  }
</script>