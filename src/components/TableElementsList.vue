<template>
  <div v-if="!isUserLoading" class="wrapper">
      <v-data-table
          :custom-filter="filterOnlyCapsText"
          v-model:page="page"
          v-model="selected"
          class="table"
          :headers="headers"
          :items="users"
          height="400"
          item-value="id"
          show-select
          :search="search"
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
    <v-btn @click="removeUsers(selected)" color="deep-purple-lighten-1" icon="mdi-delete-outline" class="cart"></v-btn>
  </div>
  <Loader v-else class="loader"></Loader>

</template>

<script>
import Loader from "~/src/components/UI/Loader.vue";

export default {
  components: {Loader},
  data () {
    return {
      page: 1,
      selected: [],
      users: [],
      isUserLoading: true,
      headers: [
        { title: 'Name', align: 'start', key: 'name' },
        { title: 'Username', align: 'end', key: 'username' },
        { title: 'Email', align: 'end', key: 'email' },
        { title: 'Phone', align: 'end', key: 'phone' },
        { title: 'City', align: 'end', key: 'address.city' },
      ],
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
    removeUsers(selected) {
      this.users = this.users.filter(user => !selected.includes(user.id))
    }
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
  .search {
    width: 100%;
  }
  .wrapper{
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
  }
  .loader {
    position: absolute;
    right: 50%;
    top: 50%;
  }
</style>