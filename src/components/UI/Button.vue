<template>
  <div>
    <v-btn variant="tonal" color="purple-darken-3">
      {{title}}
    </v-btn>
  </div>
</template>

<script>

export default {
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>

</style>