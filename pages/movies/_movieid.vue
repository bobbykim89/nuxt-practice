<template>
  <div class="container single-movie"></div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'single-movie',
  data() {
    return {
      movie: null,
    }
  },
  async fetch() {
    await this.getSingleMovie()
  },
  methods: {
    async getSingleMovie() {
      const apiKey = process.env.API_KEY
      const data = axios.get(
        `https://api.themoviedb.org/3/movie/${this.$route.params.movieid}?api_key=${apiKey}&language=en-US`
      )
      const result = await data
      this.movie = result.data
    },
  },
}
</script>

<style lang="scss" scoped></style>
