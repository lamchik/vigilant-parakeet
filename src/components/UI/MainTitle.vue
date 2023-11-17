<template>
  <div>
    <h1 class="title">{{mainTitle}}</h1>

  </div>
</template>

<script>
export default {
  props: {
    mainTitle: {
      type: String,
      required: true
    }
  }

}
</script>

<style scoped>
.title {
  color: #09224a;
  margin-bottom: 2rem;
}
</style>