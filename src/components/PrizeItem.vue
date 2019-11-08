<template>
  <li>
    <router-link :to="'/prize/' + prize.id">
      <img :src="imageUrl" :alt="prize.name"/>
      <h2>{{prize.name}}</h2>
    </router-link>
  </li>
</template>

<script>
// noinspection JSUnusedGlobalSymbols
export default {
  name: 'PrizeItem',
  props: {
    prize: {
      type: Object,
      required: true,
    },
  },
  computed: {
    imageUrl() {
      return process.env.VUE_APP_API_URL + this.prize.image_uri;
    }
  }
};
</script>

<style scoped>
img {
  max-height: 100px;
  width: auto;
}
</style>
