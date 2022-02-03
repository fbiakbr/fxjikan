<template>
  <div class="col-md-3 mb-3">
    <div class="container">
      <div class="card">
        <img :src="anime.image_url" class="card-img-top" />
        <div class="card-body">
          <h6 class="card-title">
            <strong>{{ anime.title }}</strong>
          </h6>
          <p>Episode : {{ anime.episodes }}</p>
          <p style="margin-top: -16px">Type : {{ anime.type }}</p>
          <p style="margin-top: -16px">Score : {{ anime.score }}</p>
          <p style="margin-top: -16px">Rating : {{ anime.rated }}</p>
          <a class="btn btn-primary btn-sm" :href="anime.url" target="_blank">Read More</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  props: ["anime"],
  name: "Card",
};
</script>

<style></style>
