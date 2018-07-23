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
  props: {
    partType: { type: String },
    id: {
      type: [Number, String],
      validator(value) {
        return Number.isInteger(Number(value));
      },
    },
  },
  computed: {
    part() {
      // prefer destructuring
      const { partType, id } = this;
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
