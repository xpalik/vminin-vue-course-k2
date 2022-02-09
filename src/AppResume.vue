<template>
  <div class="card card-w70">
    <h2 v-if="!contentArray[0]">Добавьте первый блок, чтобы увидеть результат</h2>
    <div v-for="(item) in contentArray">
      <h1 v-if="item.tag === 'title'">{{ item.content }}</h1>
      <h2 v-else-if="item.tag === 'subtitle'">{{ item.content }}</h2>
      <h3 v-else-if="item.tag === 'subtitle'">{{ item.content }}</h3>
      <p v-else-if="item.tag === 'text'">{{ item.content }}</p>
      <div class="avatar" v-else-if="item.tag === 'avatar'">
        <img :src="item.content">
      </div>


    </div>
  </div>
</template>

<script>
export default {
  name: "AppResume",
  props: {
    contentArray: {
      type: Array,
      default: []
    }
  }
}
</script>

<style scoped>

</style>