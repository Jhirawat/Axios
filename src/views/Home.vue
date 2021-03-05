<template>
  <div class="home">
    <!--{{ mangaList}}-->
    <div class="row">
      <MainPage
        v-for="(item, index) in mangaList.manga"
        :key="index"
        :Name="iten.title"
        :Img="item.image_url"
        :id="item.mal_id"
        class="col-3"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import MainPage from "@/components/MainPage.vue";

export default {
  name: "Home",
  components: {
    MainPage
  },
  props: {
    page: Number
  },
  data() {
    return {
      mangaList: null,
      url: `https://api.jikan.moe/v3/manga/1/characters/${this.page}`
    };
  },
  mounted() {
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
