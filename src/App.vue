<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <h3><strong>FxJikan</strong></h3>
        <p><strong>FxJikan</strong> is a simple anime search engine.</p>
        <div class="container">
          <div class="row">
            <div class="col-md-12">
              <form @submit.prevent="HandleSearch">
                <div class="input-group mb-3">
                  <input
                    type="search"
                    class="form-control"
                    placeholder="Search for an Anime"
                    v-model="search_query"
                    required
                  />
                  <button
                    class="btn btn-primary"
                    @submit.prevent="HandleSearch"
                  >
                    Search
                  </button>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
      <Card v-for="anime in animelist" :key="anime.id" :anime="anime" />
    </div>
    <div class="row">
      <div class="col-md-12 mt-3 mb-3">
        <footer>
          Build with ❤️ using Vue.js 3 and Jikan API V3 <br />
          <a href="https://github.com/fbiakbr" target="_blank">Febiadi Wisnu Akbar</a>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import Card from "./components/Card.vue";
import { ref } from "vue";

export default {
  setup() {
    const search_query = ref("");
    const animelist = ref([]);

    const HandleSearch = async () => {
      animelist.value = await fetch(
        "https://api.jikan.moe/v3/search/anime?q=" + search_query.value
      )
        .then((res) => res.json())
        .then((data) => data.results);

      search_query.value = "";
    };

    return {
      search_query,
      animelist,
      HandleSearch,
    };
  },
  name: "App",
  components: {
    Card,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap');
#app {
  font-family: "Roboto", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.card {
  text-align: left;
}
</style>
