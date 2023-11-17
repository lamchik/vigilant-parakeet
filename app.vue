<template>
  <NuxtLayout>
    <v-app class="main">
      <MainTitle :mainTitle="mainTitle"></MainTitle>
<!--      <div class="searchContainer">-->
<!--        <Search :searchTitle="searchTitle" :searchValue="searchValue"></Search>-->
<!--        <Button :title="title"></Button>-->
<!--      </div>-->

      <TableElementsList></TableElementsList>
    </v-app>
  </NuxtLayout>
</template>

<script>
import Search from "~/src/components/UI/Search.vue";
import Button from "~/src/components/UI/Button.vue";
import TableElement from "~/src/components/TableElement.vue";
import TableElementsList from "~/src/components/TableElementsList.vue";
import MainTitle from "~/src/components/UI/MainTitle.vue";

export default {
  components: {TableElementsList, Button, Search, MainTitle},
  data: () => ({
    title: 'Найти',
    mainTitle: 'Пользователи',
    searchValue: '',
    searchTitle: 'Пользователи',
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
  display: flex;
}

.searchContainer {
  display: flex;
  align-items: center;
  gap: 4rem;
}

.cart {
  margin: 1rem;


}
</style>