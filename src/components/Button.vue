<template>
  <button @click="onClick" v-bind:class="classValue" class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    type: String,
  },
  computed: {
    classValue() {
      return this.type === 'primary' ? 'button-primary' : 'button-ghost';
    },
  },
  methods: {
    onClick() {
      console.log('ola!!');
      this.$emit('onclick');
    },
  },
};
</script>

<style lang="scss">
.button {
  padding: 15px 20px;
  background: grey;
  color: black;
  cursor: pointer;

  &-primary {
    background: red;
    color: white;
  }

  &-secondary {
    background: blue;
  }

  &-ghost {
    background: white;
    color: black;
  }
}
</style>
