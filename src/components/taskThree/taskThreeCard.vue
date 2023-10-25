<template>
  <div>
    <div class="block__container">
      <div class="block__image">
        <img :src="cardData.imgSrc" class="img" />
      </div>
      <div class="block__information">
        <a :href="cardData.link" class="block__title-item">{{ cardData.title }}</a>
        <div class="block__economy"
          >Ваша экономiя: <span>{{ cardData.discount }} ₴</span></div
        >
        <div class="block__old-price"
          ><span>{{ cardData.oldPrice }} ₴</span></div
        >
        <div class="block__buy">
          <div class="block__current-price">{{ cardData.price }} ₴</div>
          <button type="submit" class="block__button">Купити</button>
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
export default {
  name: "TaskThreeCard",

  props: {
    cardData: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="css" scoped>
.block__container {
  display: flex;
  gap: 20px;
}
.img {
  width: 150px;
  height: 150px;
}
.block__information {
  display: flex;
  flex-direction: column;
  width: 400px;
}
.block__title-item {
  color: rgb(7, 115, 178);
  text-decoration: none;
}
.block__economy span {
  color: red;
}
.block__economy {
  margin-bottom: 10px;
}

.block__old-price span {
  color: rgb(130, 134, 138);
  text-decoration: line-through;
}
.block__buy {
  display: flex;
  justify-content: space-between;
}
.block__current-price {
  color: red;
  font-size: 36px;
}
.block__button {
  background-color: rgb(20, 170, 28);
  border: 0;
  border-radius: 10%;
  font-size: 16px;
  padding: 5px 15px 5px 15px;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease 0s;
}
.block__button:hover {
  background-color: rgb(13, 105, 18);
  transition: background-color 0.3s ease 0s;
}
</style>
