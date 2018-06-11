<template>
  <div class="div__style">
    <span v-for="i in numInputs" :key="i">
      <div class="sep">
        <input :class="{inputStyle:!inputStyle}" type="tel" maxLength="1" />
        <span v-show="i < numInputs">{{seperator}}</span>
      </div>
    </span>
  </div>
</template>

<script>
  export default {
    data() {
      return {};
    },
    props: {
      numInputs: {
        type: Number,
        default: 4,
        required: true
      },
      seperator: {
        type: String,
        required: false,
        default: '-'
      },
      inputStyle: {
        type: Object,
        required: false
      },
      onChange: {
        type: Function,
        required: false
      },
      disabled: {
        type: Boolean,
        required: false
      },
      shouldAutoFocus: {
        type: Boolean,
        required: false
      }
    }
  };
</script>

<style>
  .inputStyle {
    width: 1em;
    text-align: center;
    font-size: 16px;
    padding: 1.5em;
    margin: 1em;
  }
  .div__style {
    display: flex;
  }
  .sep {
    display: flex;
  }
  .sep > span {
    margin-top: 35%;
  }
</style>
