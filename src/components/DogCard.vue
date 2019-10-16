<template>
  <div class="dog-card">
    <img class="dog-card-image" :src="dog">
    <div class="dog-cart-actions">
      <button class="dog-new dog-button" @click="$emit('new')">New Dog</button>
      <button class="dog-button dog-fav" @click="$emit('fav')">Fav</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "DogCard",
  props: {
    dog: String
  }
};
</script>

