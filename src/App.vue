<template>
  <div id="app">
    <b-navbar type="dark" variant="dark">
      <b-navbar-nav id="nav">
        <router-link to="/">Home</router-link> |
      </b-navbar-nav>
      <b-nav-form class="offset-md-10">
        <b-form-input
          size="sm"
          class="mr-ms-2 col-8"
          placeholder="Search"
          v-model="sh"
        >
        </b-form-input>
        <b-button size="sm" class="my-2 my-sm-0" type="submit" @click="Search()"
          >Search</b-button
        >
      </b-nav-form>
    </b-navbar>
    <router-view :page="page" />
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      page: 1,
      sh: "",
      mangaList: null,
      url: ""
    };
  },
  methods: {
    Search() {
      const router = this.$router;
      for (let i = 0; i <= this.mangaList.manga.length; i++) {
        if (this.sh == this.mangaList.manga[i].title) {
          alert(this.mangaList.manga[i].title);
          router.push({
            path: `manga/${this.mangaList.manga[i].mal_id}`
          });
          break;
        } else if (99 == i) {
          router.push({
            path: `/`
          });
        }
      }
    },
    Page1() {
      this.page = 1;
    },
    Page2() {
      this.page = 2;
    },
    Page3() {
      this.page = 3;
    }
  },
  mounted() {
    this.url = `https://api.jikan.moe/v3/manga/1/characters/${this.page}`;
    axios
      .get(this.url)
      .then(reuslt => {
        this.mangaList = reuslt.data;
      })
      .catch(err => {
        console.log(err);
        alert(err);
      });
  }
};
</script>
