<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  props: ['msg']
}
</script>

<template>
  <button @click="count++"> {{msg}} You clicked me {{ count }} times.</button>
</template>