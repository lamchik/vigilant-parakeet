<template>
    <v-data-table
        class="table"
        :headers="headers"
        :items="ships"
        height="400"
        item-value="name"
        show-select
        v-if="!isShipLoading"
    >

    </v-data-table>
  <Loader v-else></Loader>
</template>

<script>

import Loader from "~/src/components/UI/Loader.vue";

export default {
  components: {Loader},
  data () {
    return {
      headers: [
        { title: 'Name', align: 'start', key: 'name' },
        { title: 'Max speed', align: 'end', key: 'max_atmosphering_speed' },
        { title: 'Passengers', align: 'end', key: 'passengers' },
        { title: 'Price ($)', align: 'end', key: 'cost_in_credits' },
      ],
      ships: [],
      isShipLoading: true
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
      }
      catch {
        console.log('ERROR')
      }
      finally {
        this.isShipLoading = false
      }
    },
  },
  mounted() {
    this.getShips()
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