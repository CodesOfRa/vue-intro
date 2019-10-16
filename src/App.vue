<template>
  <div class="main">
    <h1 class="title">Choose your Favorite Dog</h1>
    <div class="dog-card">
      <img class="dog-card-image" :src="dog">
      <div class="dog-cart-actions">
        <button class="dog-new dog-button" @click="randomDog">New Dog</button>
        <button class="dog-button dog-fav" @click="addToFavorite">Fav</button>
      </div>
    </div>
    <!-- <DogCard :dog="dog" @new="randomDog()" @fav="addToFavorite()"></DogCard> -->
    <div v-if="favList.length > 0">
      <h2>My Fav Dogs</h2>
      <ul>
        <li v-for="(dog,index) in favList" :key="index +'dog'" class="dog-fav-item">
          <transition name="fade" appear="true">
            <img :src="dog">
          </transition>
          <button class="dog-button dog-delete">Delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import DogCard from "./components/DogCard";
const dogs = [
  "https://images.dog.ceo/breeds/pembroke/n02113023_3474.jpg",
  "https://images.dog.ceo/breeds/terrier-sealyham/n02095889_5554.jpg",
  "https://images.dog.ceo/breeds/eskimo/n02109961_4054.jpg",
  "https://images.dog.ceo/breeds/hound-basset/n02088238_9626.jpg",
  "https://images.dog.ceo/breeds/terrier-yorkshire/n02094433_540.jpg"
];
export default {
  name: "App",
  components: {
    HelloWorld,
    DogCard
  },
  data() {
    return {
      dogs: dogs,
      pickedDog: 0,
      favList: []
    };
  },
  computed: {
    dog() {
      return dogs[this.pickedDog];
    }
  },
  mounted() {
    this.randomDog();
  },
  methods: {
    randomDog() {
      this.pickedDog = parseInt(Math.random() * this.dogs.length);
    },
    addToFavorite() {
      this.favList.push(this.dogs[this.pickedDog]);
    }
    //🦊 TODO: Add remove from favorite list
    //🦊 TODO: items in favorite list has to be unique
  }
};
</script>

<style>
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
.main {
  text-align: center;
  margin: auto;
}
.title {
  color: green;
}
.dog-card {
  border: 5px solid #6367de;
  border-radius: 10px;
  border-style: dotted;
  width: 500px;
  height: 400px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-flow: column;
  margin: auto;
}
.dog-card-image {
  padding: 1rem;
  max-width: 80%;
  max-height: 300px;
}
.dog-cart-actions {
  padding: 1rem;
}
.dog-button {
  border: none;
  height: 30px;
  border-radius: 10px;
  min-width: 100px;
  font-weight: bold;
}
.dog-new {
  background: #0cd7ed;
}
.dog-fav {
  background: #c0399f;
  color: white;
}
.dog-delete {
  background: #b00;
  color: white;
}
.dog-fav-item {
  display: flex;
  flex-flow: column;
  justify-content: space-between;
  align-items: center;
  border: 5px solid #925ace;
  border-style: dotted;
  border-radius: 10px;
  max-width: 300px;
  margin: 0.5rem;
}
.dog-fav-item img {
  max-height: 200px;
}
.main ul {
  display: flex;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
