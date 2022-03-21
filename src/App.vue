<template>
  <div class="container column">
    <PageHeader />
  </div>
  <div class="container">
    <p>
      <button class="btn primary" @click="Handler">Загрузить комментарии</button>
    </p>
    <div class="card" v-if="comments.length">
      <h2>Комментарии</h2>
      <ul class="list">
        <li v-for="comment in comments" :key="comment" class="list-item">
          <div>
            <p><strong>{{comment.email}}</strong></p>
            <small>{{comment.body}}</small>
          </div>
        </li>
      </ul>
    </div>
    <div v-if="loader" class="loader"></div>
  </div>
</template>

<script>
import PageHeader from "@/components/PageHeader";
import axios from "axios";

export default {
  name: 'App',
  emits:['actions'],
  components: {
    PageHeader
  },
  data() {
    return{
      comments: [],
      loader: false
    }
  },
  methods: {
    async Handler() {
      this.loader = true
      const response = await axios('https://jsonplaceholder.typicode.com/comments?_limit=42')
      .then(response => response.data)
      this.loader = false
      this.comments = response
    }
  }
}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
