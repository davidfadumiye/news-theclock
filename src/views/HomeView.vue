<template>
  <div>
    <h2 class="container-fluid my-3" style="--bs-text-opacity: .5;">World News</h2>
    <div class="row container-fluid my-5">
      <div class="col-3 my-2np" v-for="news in all_news" :key="news.id">
        <div class="card-group">
          <div class="card" >
            <img :src="news.multimedia[1].url" class="card-img-top" alt="..."/>
            <div class="card-body">
              <h5 class="card-title">{{ news.title }}</h5>
              <p class="card-text">{{ news.abstract }}</p>
              <p class="card-text"><small class="text-muted">{{ news.published_date }}</small></p>
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
import VueAxios from 'vue-axios'
Vue.use(VueAxios, axios)

export default {
  name: 'App',
  data () {
    return {
      all_news: []
    }
  },
  async  mounted () {
    const results = await axios.get('https://api.nytimes.com/svc/topstories/v2/world.json?api-key=pIvNRqDIX7YlwBksirwimUAqZ77d24Nm')
    console.log(results.data.results)
    this.all_news = results.data.results
  }
}
</script>
