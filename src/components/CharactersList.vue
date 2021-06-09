<template>
  <section class="characters container">
      <div class="row" v-if="!loading">
          <div 
            class="col-6 col-md-4 col-lg-3"
            v-for="character in characters"
            :key="character.id"    
            >
              <Character
                :item="character"
               />
          </div>
          
      </div>
      <Loader message="Rick & Morty app" v-else />
  </section>
</template>

<script>
import Character from './Character';
import Loader from './Loader';
import axios from 'axios';

export default {
    name: "CharactersList",
    components: {
        Character,
        Loader
    },
    data: function() {
        return {
            apiUrl: 'https://rickandmortyapi.com/api/character',
            characters: [],
            loading: true
        }
    },
    created: function() {
        axios
            .get(this.apiUrl,
            {
                params: {
                    page: 1
                }
            })
            .then(
               (response) => {
                //    console.log(response.data);
                   this.characters = response.data.results;
                //    setTimeout( () => {
                       this.loading = false;
                //    }, 3000);
                   
               }
            )
            .catch();    
    } 
}
</script>

<style>

</style>