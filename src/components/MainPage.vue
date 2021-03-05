<template>
  <div>
    <router-link :to="`/manga/${this.id}`" class="col-3">
      <b-card
        border-variant="info"
        :header="Name"
        align="center"
        style="heinght:30rem"
      >
        <b-card-text>
          <b-img :src="Img" Fluid alt="Fluid image"></b-img>
        </b-card-text>
      </b-card>
    </router-link>
  </div>
</template>
<script>
export default {
  props: {
    id: Number,
    index: Number,
    Name: String,
    Img: String
  }
};
</script>
<style></style>
