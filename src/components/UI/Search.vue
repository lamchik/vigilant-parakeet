<template>
  <v-text-field
      v-model="searchValue"
     
      label="Поиск"
      clearable
      variant="outlined"
      color="purple-darken-2"
  >
  </v-text-field>
</template>

<script>
export default {
  data() {
    return {
      searchValue: ''
    }
  },

  methods: {
    inputValue(event) {
      console.log(event)
      this.searchValue = event.target.value
    }
  }

}
</script>

<style lang="scss" scoped>

</style>
