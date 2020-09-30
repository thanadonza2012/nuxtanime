<template>
  <div>
    <!-- {{ photolist }} -->
 <v-chip-group columns>
      <v-card
        bg-variant="dark"
        v-for="list in playList"
        :key="list.mal_id"
        text-variant="white"
        class="text-center"
        style="max-width: 30rem; max-height: 100rem"
      >
        <v-card-img
          :src="list.image_url" height="150px" width="150px"></v-card-img>

        <v-card-text>{{ list.title }}</v-card-text>
        <v-card-text>{{ list.synopsis }}</v-card-text>
        <v-button :href="list.url" variant="success">web</v-button>
      </v-card>
    </v-chip-group>

    <ul>
      <li v-for="photo in photolist" :key="photo.id">
        id {{ photo.id }} : {{ photo.title }}
        <img :src="photo.thumbnailUrl" />
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      photolist: null,
      errored: false,
      loading: false,
    };
  },

  mounted() {
    axios
      .get("http://jsonplaceholder.typicode.com/photos")
      .then((response) => {
        //  this.photolist = response.data  //array 5000 รายการ
        this.photolist = response.data.slice(1, 20);
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
};
</script>

<style>
</style>