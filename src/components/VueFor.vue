<script>
export default {
  data() {
    return {
      items: [
        { message: "Foo" },
        { message: "Bar" },
        { message: "Bar1" },
        { message: "Bar1" },
      ],
    };
  },

  async created() {
    // GET request using fetch with async/await
    const response = await fetch("https://api.npms.io/v2/search?q=polymer");
    const data = await response.json();
    console.log(data);
    return data.results;
    //this.totalVuePackages = data.total;
  },
};
</script>

<template>
  <li v-for="(item, index) in items" :key="item.id">
    {{ index }} - {{ item.message }}
  </li>

  <li v-for="(item, index) in created" :key="item.id">
    {{ index }} - {{ item.package.name }}
  </li>
</template>

