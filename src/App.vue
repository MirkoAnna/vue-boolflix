<template>
  <div id="app">
    <MyHeader @search='doSearch'/>
    <MyMain :films="films" :series="series"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';

const axios = require('axios');

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data() {
    return {
      films: [],
      series: [],
      api_key: '02c85888c46eaf688c94750a58220d61',
      language: 'it-It'
    }
  },
  methods: {
    doSearch(keyword) {
      const parametri = {
        params: {
          'api_key': this.api_key,
          'query': keyword,
          'language': this.language,
        }
      };
      this.getFilms(parametri);
      this.getTv(parametri);
    },

    getFilms(params) {

      axios.get('https://api.themoviedb.org/3/search/movie/', params)
      .then((response) => {
        this.films = response.data.results;
    // handle success
    console.log(response);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  });
    },
    getTv(params) {
      
      axios.get('https://api.themoviedb.org/3/search/tv/', params)
      .then((response) => {
        this.series = response.data.results;
        // handle success
        console.log(response);
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      });
    }
  }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.css';
@import './assets/style/general.scss';
</style>
