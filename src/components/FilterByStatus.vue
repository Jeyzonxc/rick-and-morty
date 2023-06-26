<template>
  <div class="filter">
    <div class="item" @click="filter ('')">
        Todos
    </div>
    <div class="item" @click="filter ('Alive')">
        Vivos
    </div>
    <div class="item" @click="filter ('Dead')">
        Muertos
    </div>
    <div class="item" @click="filter ('unknow')">
        Desconocidos
    </div>
  </div>
</template>

<script>
import { useStore } from "vuex";
export default {
  setup() {
    const store = useStore();

    const filter = (status) => {
      store.dispatch("filterByStatus", status);
    };
    return {
        filter
    };
  },
};
</script>

<style lang="scss">
.filter {
  width: 450px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  border-radius: 20px;
  overflow: hidden;
  .item {
    padding: 1rem 1.5rem;
    background-color: var(--background-card);
    text-align: center;
    cursor: pointer;
    &:hover {
      color: var(--text-orange);
    }
  }
}
</style>
