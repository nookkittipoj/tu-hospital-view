<template>
    <v-navigation-drawer v-model="drawer"
                         fixed
                         app
                         clipped
                         class="drawer-style"
                         id="style-1">
        <v-list dense>
            <v-list-item-group v-model="item" color="primary">
                <v-list-item
                        v-for="(item, i) in items"
                        :key="i"
                        :to="item.route"
                        @click.stop="item = i"
                        link
                >
                    <v-list-item-icon>
                        <v-icon v-text="item.icon"></v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                        <v-list-item-title v-text="item.text"></v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list-item-group>
        </v-list>
    </v-navigation-drawer>
</template>

<script>
    export default {
        name: 'SideMenu',
        props: {
            api_key: String,
            drawer: Boolean
        },

        data: () => ({
            sources: [],
            errors: [],
            item: 1,
            items: [
                {text: 'Dashboard', icon: 'mdi-view-dashboard', route: '/'},
                {text: 'Equipment', icon: 'mdi-package-variant-closed', route: '/equipment'},
            ],
        }),

        created() {
        },
        methods: {}

    }
</script>

<style scoped>
    #style-1::-webkit-scrollbar {
        width: 6px;
        background-color: #F5F5F5;
    }

    #style-1::-webkit-scrollbar-thumb {
        background-color: #F90;
        background-image: -webkit-linear-gradient(90deg, rgba(255, 255, 255, .2) 25%,
        transparent 25%,
        transparent 50%,
        rgba(255, 255, 255, .2) 50%,
        rgba(255, 255, 255, .2) 75%,
        transparent 75%,
        transparent)
    }

    #style-1::-webkit-scrollbar-track {
        -webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
        background-color: #F5F5F5;
    }
</style>