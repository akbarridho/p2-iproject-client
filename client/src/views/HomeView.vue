<script>
import { mapActions, mapState } from 'pinia';
import { useUserStore } from '../stores/user';

export default {
  name: 'HomeView',
  methods: {
    ...mapActions(useUserStore, ['fetchYoutubeVideo'])
  },
  computed: {
    ...mapState(useUserStore, ['allVideo'])
  },
  created() {
    this.fetchYoutubeVideo()
  }
}
</script>

<template>
  <div class="col container1">
    <img
      src="https://dmxg5wxfqgb4u.cloudfront.net/styles/background_image_sm/s3/2022-12/011423-ufc-fight-night-imavov-vs-gastelum-SG-hero.jpg?h=d1cb525d&itok=Gw8bAKs2"
      style="width: 100%;height:688px;filter:brightness(40%);object-fit: cover;" class="img-fluid" alt="...">
    <div class="centered">
      <h3 style="margin-bottom:20px;text-align: center;font-family: Georgia, serif;font-weight: bold;">UFC FIGHT
        NIGHT</h3>
      <h1 style="font-family:Georgia, serif;font-weight: bolder;font-size: 50px;">IMAMOV VS GASTELUM</h1>
      <p style="margin-bottom:400px;text-align: center;font-family: Georgia, serif;font-weight: bold;">Elite
        Middleweight Meet at The UFC APEX to Kick Off 2023</p>
    </div>
    <!---Video Youtube--->
    <div class="d-flex w-100 justify-content-center py-3" style="background-color: black;">
      <div class="mx-2 text-center" v-for="(video, index) in allVideo" :key="`video-${index + 1}`" style="width: 400px;">
        <iframe width="400" height="230" :src="`https://www.youtube.com/embed/${video.id.videoId}`"
          frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen class="object-fit-contain"></iframe>
        <p style="color: white;">{{ video.snippet.title }}</p>
      </div>
    </div>
    <!---End Video Youtube--->
  </div>

</template>