<template>
  <div>
    <h2 class="container-fluid my-3" style="--bs-text-opacity: .5;">World News</h2>
    <div class="row container-fluid my-5">
      <div class="col-12 col-xl-3 my-2 col-md-4 col-sm-6" v-for="news in all_wrld_news" :key="news.id">
        <div class="card-group">
          <div class="card">
            <img :src="news.multimedia[1].url" class="card-img-top" alt="..." />
            <div class="card-body">
              <h5 class="card-title">{{ news.title }}</h5>
              <p class="card-text">{{ news.abstract }}</p>
              <p class="card-text"><small class="text-muted">{{ news.published_date }}</small></p>
              <a :href="news.url"><button type="button" class="btn btn-secondary">Read Article</button></a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
// import VueAxios from 'vue-axios'
Vue.use(axios)

export default {
  name: 'App',
  data () {
    return {
      all_wrld_news: []
    }
  },
  async mounted () {
    const results = await axios.get('https://api.nytimes.com/svc/topstories/v2/world.json?api-key=pIvNRqDIX7YlwBksirwimUAqZ77d24Nm')
    console.log(results.data.results)
    this.all_wrld_news = results.data.results
  }
}
</script>
