<template>
  <div class="v-screen h-screen p-16 flex items-center flex-col">
    <div class="bg-white p-8 pb-16 rounded shadow-lg mb-8">
      <h1 class="font-display flex-1 text-center" style="
        font-size: 10rem; 
        color: rgba(16, 185, 129);
        text-shadow: #fff 2px 2px 0px, rgba(16, 185, 129) 4px 4px 0px;">
          My Animal Game</h1>
    </div>
    <div>
      <button class="styled-button" v-for="t in types" :key="t" @click="setType(t)">{{ t.toUpperCase() }}</button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Menu',
  props: ['type'],
  emits: ['update:type'],
  data() {
    return {
      types: [
        'words', 
        // 'cartoon', 
        'just photos'
      ]
    }
  },
  methods: {
    setType(newType) {
      this.$emit('update:type', newType);
    }
  }
}
</script>
