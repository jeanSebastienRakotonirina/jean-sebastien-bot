<template>
  <div class="home">
    <div class="card" style="width: 18rem;">
      <img src="" class="card-img-top" alt="">
      <div class="card-body">
        <h5 class="card-title">{{ user.name }}</h5>
        <p class="card-text">{{ user.bio }}.</p>
        <a v-bind:href="user.html_url" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>
</template>

<script>

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
    const res = await fetch('https://api.github.com/users/eddiejaoude')
    this.user = await res.json()
  }
}
</script>
