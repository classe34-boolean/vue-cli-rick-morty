<template>
  <section class="characters container">
      <div class="row" v-if="!loading">

          <div class="col-12">
              <Search @performSearch="searchCharacter" />
          </div>

          <!-- 
              // altro esempio di computed
              <div class="col-12 my-4">
              <input type="text" v-model="firstName" placeholder="Inserisci il tuo nome">
              <input type="text" v-model="lastName" placeholder="Inserisci il tuo cognome">
              <h3>{{ fullName }}</h3>
          </div> -->

          <!-- <div 
            class="col-6 col-md-4 col-lg-3"
            v-for="character in characters"
            :key="character.id"    
            >
              <Character
                :item="character"
               />
          </div> -->

          <div 
            class="col-6 col-md-4 col-lg-3"
            v-for="character in filteredCharacters"
            :key="character.id"    
            >
              <Character
                :item="character"
               />
          </div>

          <div class="col-12 mb-5">
              <ResultsMessage
                :number="filteredCharacters.length"
               />
          </div>
          
      </div>
      <Loader message="Rick & Morty app" v-else />
  </section>
</template>

<script>
import Character from './Character';
import Loader from './Loader';
import Search from './Search';
import ResultsMessage from './ResultsMessage';

import axios from 'axios';

export default {
    name: "CharactersList",
    components: {
        Character,
        Loader,
        Search,
        ResultsMessage
    },
    data: function() {
        return {
            apiUrl: 'https://rickandmortyapi.com/api/character',
            characters: [],
            loading: true,
            searchFieldText: '',
            firstName: '',
            lastName: ''
        }
    },
    computed: {
        filteredCharacters: function() {
            console.log("Filtered characters");

            if(this.searchFieldText == "") {
                return this.characters;
            }

            const newArray = this.characters.filter(
                (element) => {
                    return element.name
                        .toLowerCase()
                        .includes(
                            this.searchFieldText.toLowerCase()
                        );
                } 
            );
            return newArray;
        },
        fullName: function() {
            return this.firstName + " " + this.lastName;
        }
    },
    methods: {
        searchCharacter: function(text) {
            // console.log("Click sul pulsante comunicato al componente padre");
            // console.log(text);
            this.searchFieldText = text;
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