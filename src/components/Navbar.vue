<template>
<nav>
    <v-app-bar flat app>
        <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
        <!-- logo insertion -->
        
    
        <div class="d-flex align-center">
            <v-img
            alt="Vuetify logo"
            class="shrink mr-2"
            contain
            src="https://mjoll.no/wp-content/uploads/2019/01/Mjoll-logo-blue-300.png"
            transition="scale-transition"
            width="80"
            ></v-img>
        </div>



        <!-- logo insertion -->
        <v-toolbar-title class="text-uppercase grey--text">
            <span class="font-weight-light">Todo</span>
            <span>Book</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>

        <v-menu offset-y>
            <template v-slot:activator="{ on, attrs }">
                <v-btn
                color="grey"
                text
                v-bind="attrs"
                v-on="on"
                >
                <v-icon left>expand_more</v-icon>
                <span>Menu</span>
                </v-btn>
            </template>
            <v-list >
                <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                    <v-list-item-title class="grey--text">{{ link.text }}</v-list-item-title>
                </v-list-item>
            </v-list>
        </v-menu>

        <v-btn text color="grey">
            <span>Sign Out</span>
            <v-icon right>exit_to_app</v-icon>
        </v-btn>
    </v-app-bar>

    <v-navigation-drawer app v-model='drawer' class="primary">
        <v-layout column align-center>
            <v-flex class="mt-5">
                <v-avatar size="100">
                    <img src="/avatar-4.png">
                </v-avatar>
                <p class="white--text subheading mt-2 pl-4">
                    CoolRab
                </p>
            </v-flex>
            <v-flex class="mt-4 mb-3">
                <popup />
            </v-flex>
        </v-layout>
        <v-list>
            <v-list-item v-for="link in links" :key="link.text" router :to="link.route">
                <v-list-item-action>
                    <v-icon class="white--text">d{{ link.icon }}</v-icon>
                </v-list-item-action>
                <v-list-item-content>
                    <v-list-item-title class="white--text">{{ link.text }}</v-list-item-title>
                </v-list-item-content>
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
</nav>
</template>

<script>
import Popup from './Popup.vue'

export default {
name: 'Navbar',
components: { Popup },

data: () => ({
    drawer: false,
    links: [
        { icon: 'dashboard', text: 'Dashboard', route: '/' },
        { icon: 'folder', text: 'My Projects', route: '/projects' },
        { icon: 'person', text: 'Team', route: '/team' },
      ]
    
  }),

};

</script>

<style>

</style> 
