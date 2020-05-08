<template>
  <div class="wrap-input">
    <label v-if="label">{{ label }}</label>
    <input
      :value="value"
      @input="updateInput"
      :type="type"
      :placeholder="placeholder"
      :required="required"
      :disabled="disabled"
      class="input"
    />
  </div>
</template>

<script>
export default {
  name: 'Input',
  props: {
    value: [String, Number],
    placeholder: String,
    label: String,
    type: {
      type: String,
      default: 'text',
    },
    required: {
      type: Boolean,
    },
    disabled: Boolean,
  },
  data() {
    return {
      inpValue: '',
    };
  },
  methods: {
    updateInput(value) {
      this.$emit('input', value.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
.wrap-input {
  margin-bottom: 20px;

  label {
    display: block;
    margin-bottom: 8px;
    color: #bab8cc;
    text-transform: uppercase;
  }

  .input {
    border: 1px solid #bab8cc;
    padding: 18px 10px;
    border-radius: 5px;
    width: 100%;
    color: #4e4e4e;

    &:focus {
      outline: none;
      border-color: #5640ff;
    }

    &:focus:invalid {
      border-color: red;
    }
  }
}
</style>
