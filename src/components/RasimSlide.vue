<template>
    <div class="card line">
      <img class="imgsize-small" src="@/assets/poopy.png">
    <div class="center">
      <img class="imgsize" v-bind:src="'/rasimPhoto/' + photos[i] + '.jpg'" :alt="photos[i]"/>
      <div class="block">
        <button class="btn"  @click="prevPhoto">Предыдущее фото</button>
        <button class="btn"  @click="nextPhoto">Следующее фото</button>
      </div>
    </div>
      <img class="imgsize-small" src="@/assets/clown.png">
    </div>
</template>

<script>
export default {

  data() {
    return {
      photos: [
        'rasim1', 'rasim2', 'rasim3'
      ],
      i: 0
    }
  },
  methods: {
    prevPhoto() {
      if (this.i === 0) {
        this.i = this.photos.length - 1
        console.log(this.i)
      } else {
        this.i -= 1
        console.log(this.i)
      }
    },
    nextPhoto() {
      if (this.i === this.photos.length - 1) {
        this.i = 0
      } else {
        this.i += 1
      }
    }
  }
}
</script>

<style scoped>
.line {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  align-items: center;
  justify-content: space-around;
}

.imgsize {
  width: 400px;
  height: 400px;
}

.imgsize-small {
  width: 150px;
  height: 150px;
}

.block {
  margin-top: 15px;
}
</style>