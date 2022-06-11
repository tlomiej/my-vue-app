<script>
export default {
  data() {
    return {
      items: [
        { message: "Foo" },
        { message: "Bar" },
        { message: "Bar1" },
        { message: "Bar222" },
      ],
      created: [],
    };
  },

  async mounted() {
    const response = await fetch("https://api.npms.io/v2/search?q=polymer");
    const data = await response.json();
    console.log(data);
    this.created = await data.results;

    // fetch("https://api.npms.io/v2/search?q=polymer1")
    //   .then((res) => res.json())
    //   .then((data) => (this.created = data.results));
  },
};
</script>

<template>
 <b-button size="sm" @click="toggle">
    {{ show ? 'Hide' : 'Show' }} Alert
  </b-button>
  <b-alert
    v-model="show"
    class="mt-3"
    dismissible
    @dismissed="dismissed"
  >
    Hello {{ name }}!
  </b-alert>
  
  <li v-for="(item, index) in items" :key="item.id">
    {{ index }} - {{ item.message }}
  </li>

  <li v-for="(item, index) in created" :key="item.id">
    {{ index }} - {{ item.package.name }}
  </li>
  {{ JSON.stringify(this.created) + "   aaaa" }}
</template>

