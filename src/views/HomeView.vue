<template>
  <div class="home">
    <div class="card" style="width: 18rem;">
      <img src="" class="card-img-top" alt="">
      <div class="card-body">
        <h5 class="card-title">{{ user.title }}</h5>
        <img :src="user.imgSrc" class="card-text" />
        <a v-bind:href="user.url" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HomeView',
  components: {
  },
  data () {
    return {
      user: {}
    }
  },
  async mounted () {
    const res = await axios({
      method: 'get',
      url: 'https://github.com/jsr029/rjs-portfolio/blob/master/portfolio.json',
      headers: {
        'Content-Type': 'application/json',
        'Access-Control-Allow-Origin': '/'
      },
      crossdomain: true
    })
    this.user = await res.json()
  }
}
</script>
