<template>
    <v-app light>
        <SideMenu :drawer="drawer"></SideMenu>
        <!--add this component in the template -->
        <v-app-bar fixed app light clipped-left color="primary" class="elevation-2">
            <v-app-bar-nav-icon @click="drawer = !drawer" class="white--text"></v-app-bar-nav-icon>
            <v-toolbar-title class="white--text">News App</v-toolbar-title>
        </v-app-bar>
        <v-content>
            <v-container fluid>
                <router-view/>
            </v-container>
        </v-content>
        <v-footer color="primary lighten-1"
                  padless
                  absolute
                  app
        >
            <v-card
                    flat
                    tile
                    width="100%"
                    class="primary lighten-1 text-center"
            >
                <v-divider></v-divider>

                <v-card-text class="white--text">
                    {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
                </v-card-text>
            </v-card>
        </v-footer>
    </v-app>
</template>

<script>
    import SideMenu from './components/SideMenu.vue' // import the SideMenu component
    export default {

        components: {
            SideMenu
        },
        data() {
            return {
                drawer: this.$vuetify.breakpoint.lgAndUp,
            }
        },
    }
</script>
