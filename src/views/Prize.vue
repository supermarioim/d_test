<template>
  <div v-if="prize">
    <h1>{{prize.name}}</h1>
    <h2>{{prize.subtitle}}</h2>
    <img :src="imageUrl" :alt="prize.name"/>
    <div v-html="prize.description"></div>
  </div>
</template>

<script>
// noinspection JSUnusedGlobalSymbols
export default {
  name: 'Prize',
  data() {
    return {
      prize: null,
    }
  },
  created() {
    this.$http.get('prizes/teaser/' + this.$route.params.prizeId)
      .then((res) => {
        this.prize = res.data.prize;
      });
  },
  computed: {
    imageUrl() {
      return process.env.VUE_APP_API_URL + this.prize.image_uri;
    }
  }
};
</script>

<style scoped>

</style>
