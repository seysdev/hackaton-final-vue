<template>
  <button @click="onClick" :class="classValue" class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'Button',
  props: {
    type: String,
    fullWidth: {
      type: Boolean,
    },
  },
  computed: {
    classValue() {
      return {
        'button-primary': this.type === 'primary',
        'button-secondary': this.type === 'secondary',
        'button-ghost': this.type === 'ghost',
        'button-full': this.fullWidth === true,
      };
    },
  },
  methods: {
    onClick() {
      this.$emit('onclick');
    },
  },
};
</script>

<style lang="scss" scoped>
.button {
  padding: 15px 20px;
  background: grey;
  color: #fff;
  border: 1px solid #fff;
  cursor: pointer;
  text-align: center;
  border-radius: 25px;

  &-primary {
    background: #5640ff;
  }

  &-secondary {
    background: #ff1558;
  }

  &-full {
    display: block;
    width: 100%;
  }

  &-ghost {
  }
}
</style>
