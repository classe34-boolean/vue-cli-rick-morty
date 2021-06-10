<template>
  <form class="d-flex mb-5">
      <div class="flex-grow-1">
          <input 
            type="text"
            class="form-control" 
            placeholder="Cerca un personaggio"
            v-model.trim="searchText"
            @keyup="$emit('performSearch', searchText)"
            >
            <!-- @keyup="$emit('performSearch', searchText)" -->
            <!-- <h4>Stai cercando: {{ uppercaseText }}</h4> -->
      </div>
      <div class="ms-3">
          <button 
            type="submit" 
            class="btn btn-primary"
            @click.prevent="$emit('performSearch', searchText)"
            >
                Cerca
            </button>
      </div>
      <div class="ms-3">
          <button 
            type="reset" 
            class="btn btn-warning"
            @click="resetSearch"
            >
                Reset
            </button>
      </div>
  </form>
</template>

<script>
export default {
    name: "Search",
    data: function() {
        return {
            searchText: '',
        }
    },
    computed: {
        uppercaseText: function() {
            return this.searchText.toUpperCase();
        }
    },
    methods: {
        search: function() {
            console.log("Ricerca");
        },
        resetSearch: function() {
            this.searchText = "";
            // this.search();
            this.$emit('performSearch', this.searchText);
        }
    }
}
</script>

<style>

</style>