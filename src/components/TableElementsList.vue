<template>
    <v-data-table
        class="table"
        :headers="headers"
        :items="ships"
        height="400"
        item-value="name"
        show-select
    >

    </v-data-table>
  <button class="button" @click="getShips"></button>
</template>

<script>

export default {
  data () {
    return {
      headers: [
        { title: 'Name', align: 'start', key: 'name' },
        { title: 'Max speed', align: 'end', key: 'year' },
        { title: 'Birth year', align: 'end', key: 'passengers' },
        { title: 'Price ($)', align: 'end', key: 'price' },
      ],
      ships: []
    }
  },
  methods: {
    async getShips() {
      try {
        const response = await fetch('https://swapi.dev/api/starships', {
          method: "GET"
        })
        const res = await response.json()
        this.ships = res.results
         console.log(await res.results)
      }
      catch {
        console.log('ERROR')
      }
    },
  }


}
</script>

<style>
  .table {
    height: 90vh;
  }
  .button {
    width: 100px;
    height: 100px;
    background-color: coral;
  }
</style>