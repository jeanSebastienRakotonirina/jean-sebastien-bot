<template>
  <div class="row row-cols-1 row-cols-lg-3 align-items-stretch g-4 py-5"
  style="width:100%; margin: 0 auto;"
  >
    <div class="col" v-for="pro in projects" :key="pro.id">
      <div class="card card-cover h-100 overflow-hidden text-bg-dark rounded-4 shadow-lg"
        :style="{ background: 'url(' + pro.imgSrc + ') no-repeat'}"
        style="background-size: cover; border-radius: 10px !important;padding: 2px;border: 2px solid black;"
        >
        <div class="d-flex flex-column h-100 p-5 pb-3 text-blue text-shadow-1">
          <h3 class="pt-5 mt-5 mb-4 display-6 lh-1 fw-bold"
          style="text-shadow: 2px 2px 2px green;"
          >{{ pro.title }}</h3>
          <ul class="-flex list-unstyled mt-auto">
            <button @click="handleClick(pro.url)" class="btn btn-success">+ Détails</button>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'HomeView',
  components: {
  },
  data: function () {
    return {
      projects: {}
    }
  },
  computed: {
    styles: function () {
      return this.projects.map(m => m.imgSrc)
    }
  },
  mounted: async function () {
    const res = await fetch('https://jeansebastienrakotonirina.github.io/portfolioApi/projects.json')
    this.projects = await res.json()
  },
  methods: {
    handleClick: function (url) {
      window.open(url)
    }
  }
}
</script>
