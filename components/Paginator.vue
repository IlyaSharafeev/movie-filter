<template>
  <vue-awesome-paginate
      v-if="movieStore.getTotalPages"
      :total-items="movieStore.getTotalPages"
      :items-per-page="1"
      :max-pages-shown="5"
      :on-click="onClickHandler"
      :hide-prev-next="true"
  />
</template>

<script lang="ts" setup>
import {useMoviesStore} from "~/store/movies";

const emit = defineEmits([
    'clickHandler',
])

const movieStore = useMoviesStore();

const onClickHandler = (page: number) => {
  movieStore.setMovies(page);
  emit('clickHandler', page)
};
</script>

<style lang="scss">
.pagination-container {
  display: flex;
  column-gap: 10px;
}
.paginate-buttons {
  height: 40px;
  width: 40px;
  border-radius: 20px;
  cursor: pointer;
  background-color: rgb(242, 242, 242);
  border: 1px solid rgb(217, 217, 217);
  color: black;
}
.paginate-buttons:hover {
  background-color: #d8d8d8;
}
.active-page {
  background-color: #3498db;
  border: 1px solid #3498db;
  color: white;
}
.active-page:hover {
  background-color: #2988c8;
}
</style>