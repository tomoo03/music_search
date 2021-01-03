<template>
  <v-container>
    <v-layout
      text-center
      wrap>

      <v-flex mb-4>
        <h1 class="display-2 font-weight-bold mb-3">
          音楽検索
        </h1>
        <v-text-field
          v-model="keyword"
          :counter="100"
          label="アーティスト名を入力して下さい。"
          required
        ></v-text-field>

        <v-btn @click="search">検索</v-btn>
      </v-flex>

    </v-layout>
  </v-container>
</template>

<script>
// @ is an alias to /src

export default {
  data() {
    return {
      keyword: ''
    }
  },
  methods: {
    search() {
      this.$router.push(`/result/${this.keyword}`)
    }
  }
}
</script>
