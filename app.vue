<template>
  <NuxtLayout>
    <v-app class="main">
      <div class="searchContainer">
        <Search></Search>
        <Button :title="title"></Button>
      </div>
      <v-card
          class="mx-auto"
          max-width="300"
      >
      </v-card>
      <TableElementsList></TableElementsList>
    </v-app>
  </NuxtLayout>
</template>

<script>
import Search from "~/src/components/UI/Search.vue";
import Button from "~/src/components/UI/Button.vue";
import TableElement from "~/src/components/TableElement.vue";
import TableElementsList from "~/src/components/TableElementsList.vue";

export default {
  components: {TableElementsList, Button, Search},
  data: () => ({
    title: 'Найти',

  }),
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.main {
  margin: 5rem;
}

.searchContainer {
  display: flex;
  align-items: center;
  gap: 4rem;
}
</style>