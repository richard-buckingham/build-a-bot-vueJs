<template>
  <div>
    <h1>{{part.title}}</h1>
    <div>
      {{part.description}}
    </div>
  </div>
</template>

<script>
// import the parts
import parts from '../data/parts';

export default {
  name: 'PartInfo',
  computed: {
    part() {
      // const partType = this.$route.params.partType;
      // const id = this.$route.params.id;

      // prefer destructuring
      const { partType, id } = this.$route.params;
      console.log('partType = ', partType);
      console.log('id = ', id);

      // remember that params pulled off a route are always strings,
      // so we need to convert the id to an integer
      return parts[partType].find(part => part.id === +id);
    },
  },
};
</script>

<style scoped>
</style>
