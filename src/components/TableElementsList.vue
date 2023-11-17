<template>
  <div class="wrapper">
      <v-data-table
          :custom-filter="filterOnlyCapsText"
          v-model:page="page"
          class="table"
          :headers="headers"
          :items="users"
          height="400"
          item-value="name"
          show-select
          :search="search"
          v-if="!isUserLoading"
          items-per-page="6"
      >
        <template v-slot:top>
          <v-text-field
              v-model="search"
              label="Поиск"
              class="search"
          ></v-text-field>
        </template>
      </v-data-table>
    <Loader v-else class="loader"></Loader>
    <v-btn v-if="!isUserLoading" @click="" color="deep-purple-lighten-1" icon="mdi-delete-outline" class="cart"></v-btn>
  </div>

</template>

<script>

import Loader from "~/src/components/UI/Loader.vue";

export default {
  components: {Loader},
  data () {
    return {
      page: 1,
      headers: [
        { title: 'Name', align: 'start', key: 'name' },
        { title: 'Username', align: 'end', key: 'username' },
        { title: 'Email', align: 'end', key: 'email' },
        { title: 'Phone', align: 'end', key: 'phone' },
        { title: 'City', align: 'end', key: 'address.city' },
      ],
      users: [],
      isUserLoading: true,
      search: ''
    }
  },
  methods: {
    async getUsers() {
      try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/users`, {
          method: "GET"
        })
        this.users = await response.json()
      }
      catch {
        console.log('ERROR')
      }
      finally {
        this.isUserLoading = false
      }
    },
    filterOnlyCapsText (value, query, item) {
      return value != null &&
          query != null &&
          typeof value === 'string' &&
          value.toString().indexOf(query) !== -1
    },
  },
  mounted() {
    this.getUsers()
  }
}
</script>

<style>
  .table {
    height: 50vh;
    display: flex;
    align-items: flex-start;
  }
  .wrapper{
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
  }
  .loader{
    position: absolute;
    left: 50%;
    top: 50%;
  }
  .search {
    width: 100%;
  }
</style>