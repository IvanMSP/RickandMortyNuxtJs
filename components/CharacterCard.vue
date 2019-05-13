<template>
<div class="column is-one-quarter">
    <div class="box">
        <article class="media">
      <div class="media-left">
        <figure class="image is-64x64">
          <img class="is-rounded" :src="character.image" :alt="character.name">
        </figure>
      </div>
      <div class="media-content">
        <div class="content">
          <p>
            <strong>{{character.name}}</strong> 
            <br>
            <span class="icon has-text-info">
                <font-awesome-icon :icon="['fas', 'venus-mars']"/>
            </span>
            <small>{{character.gender}}</small>
            <br>
            <span class="icon has-text-info">
                <font-awesome-icon :icon="['fas', 'heartbeat']"/>
            </span>
            <small>{{character.status}}</small>
            <br>
            <span class="icon has-text-info">
                <font-awesome-icon :icon="['fas', 'location-arrow']"/>
            </span>
            <small>{{character.origin.name}}</small>
          </p>
        </div>
        <nav class="level is-mobile">
            <div class="level-left">
                <nuxt-link :to="`character/${character.id}`" class="button is-small is-primary is-rounded">
                  <span class="icon has-text-white">
                      <font-awesome-icon :icon="['fas', 'chevron-right']"/>
                  </span>
                  <span>More info</span>
                </nuxt-link>
            </div>
        </nav>
      </div>
      </article>
    </div>
</div>
</template>

<script>
export default {
    name:'CharacterCard',
    props:{
        character: Object
    }
}
</script>

<style scoped>
.content{
    min-height: 9.5em;
}
</style>
