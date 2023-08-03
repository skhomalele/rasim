<template>
  <div class="form-control" @submit.prevent="createComment">
    <form class="card">
      <p>
        <input type="text" class="comment-form" v-model="comment" placeholder="Выплесни эмоции!">
      </p>

      <div class="inputs">
        <p class="name-input">
          <label for="name"></label>
          <input type="text" id="name" v-model.trim="name" placeholder="Как тебя зовут?" required>
        </p>
      </div>
      <button class="btn" type="submit">Поделиться</button>
    </form>
  </div>
</template>

<script>
import axios from "axios"

<!--export default {-->
<!--  data() {-->
<!--    return {-->
<!--      name: '',-->
<!--      comment: '',-->
<!--      comments: []-->
<!--    }-->
<!--  },-->
<!--  methods: {-->
<!--     async createComment() {-->
<!--       try {-->
<!--         const response = await axios.post('https://commet-for-rasim-default-rtdb.europe-west1.firebasedatabase.app/comment.json', {-->
<!--           name: this.name,-->
<!--           comment: this.comment,-->
<!--           // id: Date.now()-->
<!--         })-->
<!--         console.log(response)-->
<!--         this.name = ''-->
<!--         this.comment = ''-->
<!--       } catch (e) {-->
<!--         console.log(e)-->
<!--       }-->
<!--     },-->
<!--  },-->
<!--}-->
<!--</script>-->

<!--<style scoped>-->
<!--.comment-form {-->
<!--  height: 100px;-->
<!--}-->

<!--.name-input {-->
<!--  width: 200px;-->
<!--  display: flex;-->
<!--  justify-content: center;-->
<!--  align-items: center;-->
<!--  flex-direction: column;-->
<!--}-->

<!--.photo-input {-->
<!--  width: 200px;-->
<!--  border: 2px solid grey;-->
<!--  border-radius: 10px;-->
<!--  display: flex;-->
<!--  align-items: center;-->
<!--  justify-content: center;-->
<!--  background: white;-->
<!--  margin-left: 20px;-->
<!--}-->

<!--.photo-input input {-->
<!--  display: none;-->
<!--}-->

<!--.inputs {-->
<!--  display: flex;-->
<!--  flex-direction: row;-->
<!--}-->

<!--.inputs p {-->
<!--  margin-top: 0;-->
<!--}-->
<!--</style>-->