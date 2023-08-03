<template>
  <div class="container">
  <div class="title">
    <h1>Сайт для тех, кто пострадал от Расима</h1>
  </div>
  <rasim-slide></rasim-slide>
    <comment-list></comment-list>
  </div>
</template>

<script>
import RasimSlide from "@/components/RasimSlide";

import CommentList from "@/components/CommentList";
export default {
  components: {RasimSlide, CommentList},
  }
</script>

<style scoped>

</style>