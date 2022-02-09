<template>

    <form class="card card-w30" @submit.prevent="submitForm">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Значение</label>
        <textarea id="value" rows="3" v-model="textAreaText"></textarea>
      </div>

      <button class="btn primary" :disabled="buttonDisabled">Добавить</button>
    </form>


</template>

<script>
export default {
  name: "AppLeftBlock",
  data() {
    return {
      textAreaText: ''
      }
    },
  emits: ['addItem'],
  methods: {
    submitForm(event) {
      this.$emit('addItem', event)
      this.textAreaText = ''
    },
  },
  computed: {
    buttonDisabled() {
      if (this.textAreaText.length >= 3) {
        return false
      } else {
        return true
      }
    }
  }
}
</script>

<style scoped>

</style>