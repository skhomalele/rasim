<template>
  <div class="card">
    <h2>Давайте выскажем ему все, что о нем думаем!</h2>
    <div class="form-control" @submit.prevent="createComment">
      <form class="card">
        <p>
          <input type="text" class="comment-form" v-model="commentInput" placeholder="Выплесни эмоции!">
        </p>

        <div class="inputs">
          <p class="name-input">
            <label for="name"></label>
            <input type="text" id="name" v-model.trim="nameInput" placeholder="Как тебя зовут?">
          </p>
        </div>
        <button class="btn" type="submit" :disabled="nameInput.length < 2 || commentInput.length < 3">Поделиться</button>
      </form>
    </div>
  </div>
  <div class="card">
    <h2>Комментарии пострадавших от Расима</h2>
    <div class="reverse" v-if="comments.length !== 0">
      <div class="card inline" v-for="comment in comments" :key="comment.id" >
        <div>
          <h3>{{comment.name}}</h3>
          <p>{{comment.comment}}</p>
        </div>
        <button class="btn danger" @click="removeComment(comment.id)">Удолить хуйню!</button>
      </div>
    </div>
    <div v-else> <h4>Пока что комментов нет, стань первым!</h4></div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      nameInput: '',
      commentInput: '',
      comments: []
    }
  },
  methods: {

    async createComment() {
      try {
        const response = await axios.post('https://commet-for-rasim-default-rtdb.europe-west1.firebasedatabase.app/comment.json', {
          name: this.nameInput,
          comment: this.commentInput,
        })
        this.comments.push({
          name: this.nameInput,
          comment: this.commentInput,
          id: response.data.name
        })
        console.log(response)
        this.nameInput = ''
        this.commentInput = ''
      } catch (e) {
        console.log(e)
      }
    },

    async fetchComment() {
      try {
        const {data} = await axios.get('https://commet-for-rasim-default-rtdb.europe-west1.firebasedatabase.app/comment.json')
        this.comments = Object.keys(data).map(key => {
          return {
            id: key,
            ...data[key]
          }
        })
        console.log(this.comments)

      } catch (e) {
        console.log(e)
      }
    },
    async removeComment(id) {
      await axios.delete (`https://commet-for-rasim-default-rtdb.europe-west1.firebasedatabase.app/comment/${id}.json`)
      this.comments = this.comments.filter(comment => comment.id !== id)
      // await this.fetchComment()
      console.log(this.comments)
    }
  },
  mounted() {
    this.fetchComment()
  },
}
</script>

<style scoped>

.comment-form {
  height: 100px;
}

.name-input {
  width: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.photo-input {
  width: 200px;
  border: 2px solid grey;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  margin-left: 20px;
}

.photo-input input {
  display: none;
}

.inputs {
  display: flex;
  flex-direction: row;
}

.inputs p {
  margin-top: 0;
}

.reverse {
  display: flex;
  flex-direction: column-reverse;
}

.inline {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>