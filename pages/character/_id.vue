<template>
<section class="hero is-medium is-primary is-bold">
    <div class="hero-body">
        <div class="container">
            <div class="columns is-centered">
                <div class="column is-half">
                    <img class="is-rounded" :src="character.image" :alt="character.name">
                    <h1 class="title">
                        {{ character.name }}
                    </h1>
                    <h2 class="subtitle">
                        {{ character.status }}
                    </h2>
                    <nuxt-link to="/" class="button is-small is-dark is-rounded">
                        <span class="icon has-text-white">
                            <font-awesome-icon :icon="['fas', 'chevron-left']"/>
                        </span>
                        <span>characters</span>
                    </nuxt-link>
                </div>
            </div>
            <div class="tabs is-centered">
                <ul>
                    <li><a>Location</a></li>
                    <li><a>Episodes</a></li>
                    <li><a>Created</a></li>
                </ul>
            </div>
            <div>
                <p>{{location.name}} - {{location.type}}</p>            
            </div>
        </div>
    </div>
</section>

</template>

<script>
//Import Libraries
import router from 'vue-router'
import axios from 'axios';

//Import endpoint base
import env from '../../config/env';

export default {
    name: 'CharacteIdvPage',
    data(){
        return{
            character:{},
            location:{}
        }
    },
    created(){
        axios.get(`${env.endpoint}/character/${this.$route.params.id}`).then(characterResponse => {
            this.character = characterResponse.data;
            console.log(this.character.location.url)
        }),
        axios.get(`https://rickandmortyapi.com/api/location/20`).then(LocationResponse => {
            this.location = LocationResponse.data;
            console.log(LocationResponse.data)
        })

    }
}
</script>

<style scoped>
.is-half{
    text-align:center;
    align-content: center;
}
</style>
