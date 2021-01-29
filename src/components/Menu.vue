<template>
  <div>
    <h1>The Animal Game</h1>
    <template v-for="t in types" :key="t">
      <button @click="setType(t)">{{ t.toUpperCase() }}</button>
    </template>
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
        'word', 
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
