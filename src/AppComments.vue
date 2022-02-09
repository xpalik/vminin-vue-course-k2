<template>
  <div class="container">
    <p>
      <button class="btn primary" @click="loadComments">Загрузить комментарии</button>
    </p>
    <div class="card" v-if="comments[0]">
      <h2>Комментарии</h2>
      <ul class="list">
        <li class="list-item" v-for="item in comments">
          <div>
            <p><strong>{{ item.email }}</strong></p>
            <small>{{ item.body }}</small>
          </div>
        </li>
      </ul>
    </div>
    <div class="loader" v-if="loadingBar"></div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "AppComments",
  data() {
    return {
      loadingBar: false
    }
  },
  props: {
    comments: Array,
    default: []
  },
  methods: {
    async loadComments() {
      this.loadingBar = true
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      setTimeout(() => {
        for (const item of data) {
          this.comments.push({email: item.email, body: item.body})
        }
        this.loadingBar = false
      }, 2000)
    }
  }
}
</script>

<style scoped>

</style>