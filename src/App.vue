<template>
  <div class="container column">
    <app-left-block
        @addItem="addItem"
        v-model="value"

    ></app-left-block>
    <app-resume :contentArray="contentArray"></app-resume>
  </div>
  <app-comments :comments="comments"></app-comments>
</template>

<script>
import AppLeftBlock from "./AppLeftBlock";
import AppResume from "./AppResume";
import AppComments from "./AppComments";
export default {
  data() {
    return {
      data: null,
      value: null,
      contentArray: [],
      comments: []
    }
  },
  methods: {
    addItem(event) {
      this.contentArray.push({
        tag: event.target.type.value,
        content: event.target.value.value
      })
    }
  },
  components: {AppLeftBlock, AppResume, AppComments}
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
