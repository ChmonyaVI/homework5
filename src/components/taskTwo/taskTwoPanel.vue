<template>
  <div class="flex">
    <task-two-card v-for="card in cardsListData" :key="card.id" :card-data="card" />
  </div>
</template>

<script>
import taskTwoCard from "./taskTwoCard.vue";

export default {
  name: "taskTwoPanel",

  components: { taskTwoCard },

  props: {
    cardsListData: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="css" scoped>
.flex {
  padding-top: 30px;
  padding-bottom: 30px;
  display: flex;
  justify-content: center;
  gap: 5px;
  background-color: rgb(11, 28, 44);
}
</style>
