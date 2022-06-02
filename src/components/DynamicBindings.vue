<script>
export default {
  data() {
    return {
      titleClass: 'title'
    }
  }
}
</script>

<template>
<button @click="titleClass = 'titleGreen'"> Green</button>
<button @click="titleClass = 'titleRed'"> Red</button>
  <h1 :class="titleClass">Make me red</h1>
</template>

<style>
.titleRed {
  color: red;
}

.titleGreen {
  color: green;
}
</style>