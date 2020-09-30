<template>
  <div>
    <br />
    <br />
    <input type="text" v-model="textSearch" />
    <button @click="searchData()">Search</button>
    <br />
    <br />
    <br />
    <br />
    <br />


    <v-card
      class="mx-auto"
      max-width="344"
      v-for="list in playList"
      :key="list.mal_id"
    >
      <v-img
        :src="list.image_url"
        class="rounded-0"
        style="max-width: 30rem; max-height: 50rem"
      ></v-img>

      <v-card-title>
        {{ list.title }}
      </v-card-title>
      <v-btn color="orange lighten-2" text> Explore </v-btn>

      <v-spacer></v-spacer>

      <v-expand-transition>
        <v-divider></v-divider>
      </v-expand-transition>
    </v-card>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      playList: null,
      textSearch: '',
      list: null,
    }
  },

  methods: {
    searchData() {
      axios
        .get(
          'https://api.jikan.moe/v3/search/anime?q=' +
            this.textSearch +
            '&limit=10'
        )
        .then((response) => {
          this.playList = response.data.results
        })
        .catch((err) => {
          console.log(err)
        })
    },
  },
}
</script>

<style>
</style>