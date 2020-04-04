<template>
    <v-layout row wrap align-center>
        <v-flex xs8 offset-md2>
            <div v-for="article in articles" :key="article.title">
                <v-card class="my-3" hover data-aos="zoom-in" data-aos-easing="ease">
                    <v-img
                            height="350px"
                            v-bind:src="article.urlToImage"
                    ></v-img>
                    <v-container fill-height fluid>
                        <v-layout>
                            <v-flex xs12 align-end d-flex>
                                <span class="headline">{{ article.title }}</span>
                            </v-flex>
                        </v-layout>
                    </v-container>
                    <v-card-text>
                        {{ article.description }}
                    </v-card-text>
                    <v-card-actions>
                        <v-chip small color="secondary" class="white--text">
                            {{article.source.name}}
                        </v-chip>
                        <v-spacer></v-spacer>
                        <v-btn icon class="red--text">
                            <v-icon small>fa-reddit</v-icon>
                        </v-btn>
                        <v-btn icon class="light-blue--text">
                            <v-icon small>fa-twitter</v-icon>
                        </v-btn>
                        <v-btn icon class="blue--text text--darken-4">
                            <v-icon small>fa-facebook</v-icon>
                        </v-btn>
                        <v-btn icon class="red--text">
                            <v-icon small>fa-google-plus</v-icon>
                        </v-btn>
                        <v-btn icon class="blue--text text--darken-4">
                            <v-icon small>fa-linkedin</v-icon>
                        </v-btn>
                        <v-spacer></v-spacer>

                        <v-btn small replace color="info" v-bind:href="article.url" target="_blank">Read More</v-btn>
                    </v-card-actions>
                </v-card>
            </div>
        </v-flex>
    </v-layout>
</template>

<script>
    import axios from "axios";

    export default {
        name: "MainContent",
        data() {
            return {
                api_key: '6bd6c9a75fdb47b888def4eaec38d6c2',
                articles: [],
                errors: []
            }
        },
        created() {
            axios.get('https://newsapi.org/v2/top-headlines?sources=techcrunch&apiKey=' + this.api_key)
                .then(response => {
                    this.articles = response.data.articles
                    console.log('data:')
                    console.log(response.data.articles) // This will give you access to the full object
                })
                .catch(e => {
                    this.errors.push(e)
                })
        },
        //add the methodes events hadler with setResource() function
        methods: {
            setResource(source) {
                axios.get('https://newsapi.org/v2/top-headlines?sources=' + source + '&apiKey=' + this.api_key)
                    .then(response => {
                        this.articles = response.data.articles
                        console.log(response.data)
                    })
                    .catch(e => {
                        this.errors.push(e)
                    })

            }
        }
    }
</script>

<style scoped>

</style>