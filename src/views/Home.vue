<template>
  <div class="home">
    <h1 v-if="date">Promotion starts: {{date}}</h1>
    <ul>
      <prize-item v-for="prize in prizes" :key="prize.id" :prize="prize"/>
    </ul>
  </div>
</template>

<script>
import moment from 'moment'
import PrizeItem from '../components/PrizeItem.vue'

export default {
  name: 'home',
  components: { PrizeItem },
  data() {
    return {
      prizes: [],
      date: null,
    }
  },
  created() {
    this.$http.get('prizes/teaser')
      .then((res) => {
        this.prizes = res.data.prizes;
      });

    this.$http.get('settings/promotion')
      .then((res) => {
        this.date = moment(res.data.promotion_start).format('D.M.YYYY.')
      });
  }
}
</script>
