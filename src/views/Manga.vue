<template>
  <div class="container col-10" style="heinght: 60rem">
    <div class="row">
      <div class="col-3">
        <b-img
          thumbnail
          fluid
          :src="mangaList.image_url"
          alt="fluid image"
          style="heinght: 40 rem; width: 30rem"
        >
        </b-img>
        <b class="Name-Manga">
          {{ mangaList.title }} ( {{ mangaList.title_japanese }} )</b
        >
        <div class="row Genres">
          <b>Genres:</b>
          <b
            v-for="(itime, index) in mangaList.genres"
            :key="index"
            class="offset-md-1"
          >
            {{ item.name }}
          </b>
        </div>
      </div>
      <div class="col-8">
        <p class="Trailer-Manga">
          {{ mangaList.synopsis }}
        </p>
        <iframe width="420" height="345" :src="mangaList.trailer_url"></iframe>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      mangaList: null,
      url: `https://api.jikan.moe/v3/manga/1/characters/${this.route.params.id}`
    };
  },
  mounted() {
    axios
      .get(this.url)
      .then(result => {
        this.mangaList = result.data;
      })
      .catch(err => {
        console.log(err);
        alert(err);
      });
  }
};
</script>

<style>
.Name-Manga {
  color: #000;
  font-size: 40px;
  text-shadow: 2px 2ex rgb(16, 19, 163);
}
.Trailer-Manga {
  color: rgb(255, 255, 255);
  font-size: 25px;
}
.Genres {
  color: rgb(84, 50, 235);
  font-size: 18px;
}
</style>
