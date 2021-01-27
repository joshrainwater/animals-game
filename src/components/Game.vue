<template>
  <div>
    <img class="w-16 h-16" :src="currentPhoto" alt="">
    <div v-for="guess in guesses" :key="guess">
      <button v-if="guess == randomSorted[index]" @click="right()">* {{ guess }}</button>
      <button v-else @click="wrong()">{{ guess }}</button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Game',
  props: {
    animals: Object,
    type: String
  },
  data() {
    return {
      index: 0
    }
  },
  computed: {
    randomSorted() {
      let arr = Object.keys(this.animals);
      for (let i = arr.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [arr[i], arr[j]] = [arr[j], arr[i]];
      }
      return arr;
    },
    currentPhoto() {
      let animal = this.animals[this.randomSorted[this.index]];
      let pic = Math.floor(Math.random() * animal.pictures.length);
      return animal.pictures[pic].url;
    },
    guesses() {
      let guesses = [this.randomSorted[this.index]];
      let possible = [...this.randomSorted];
      possible.splice(this.index, 1);
      for (let i = 0; i <=1 ; i++) {
        let guess = Math.floor(Math.random() * possible.length);
        guesses.push(possible[guess]);
        possible.splice(guess, 1);
      }

      for (let i = guesses.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [guesses[i], guesses[j]] = [guesses[j], guesses[i]];
      }
      return guesses;
    } 
  },
  methods: {
    right() {
      if(this.index == Object.keys(this.animals).length-1) {
        this.index = 0;
      } else {
        this.index++;
      }
    },
    wrong() {
      console.log('wrong sucka');
    }
  }
}
</script>
