<template>
  <v-container>
    <v-layout
      text-center
      wrap>

      <v-flex mb-4>
        <h1 class="display-2 font-weight-bold mb-3">
          検索結果
        </h1>
        <p>検索キーワード:{{ $route.params.keyword }}</p>
      </v-flex>

      <v-flex
        mb-5
        xs12
      >
        <div style="margin-bottom: 10px;" v-for="(album, i) in albums"
            :key="i">
          <v-card
            color="black"
            dark
            :href="album.collectionViewUrl"
            target="_blank"
          >
            <v-list-item three-line>
              <v-list-item-content class="align-self-start">
                <v-list-item-title
                  class="headline mb-2"
                  v-text="album.collectionName"
                >
                </v-list-item-title>

                <v-list-item-subtitle v-text="album.artistName"></v-list-item-subtitle>
              </v-list-item-content>

              <v-list-item-avatar
                size="125"
                tile
              >
                <v-img :src="album.artworkUrl100"></v-img>
              </v-list-item-avatar>
            </v-list-item>
          </v-card>
          </div>

      </v-flex>

    </v-layout>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      albums: []
    }
  },
  created() {
    const vm = this;
    axios.get(`https://itunes.apple.com/search?term=${this.$route.params.keyword}&entity=album`)
      .then(response => {
        console.log(response);
        vm.albums = response.data.results;
      });
  }
};
</script>
