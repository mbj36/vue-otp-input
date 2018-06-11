<template>
  <div class="div__style">
    <span v-for="i in numInputs" :key="i">
      <div>
        <input class="__input-style" type="tel" maxLength="1" /> {{seperator}}
      </div>
    </span>
  </div>
</template>

<script>
  export default {
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
  .__input-style {
    width: 1em;
    text-align: center;
    font-size: 16px;
    padding: 1.5em;
    margin: 1em;
  }
  .div__style {
    display: flex;
    margin: 0 auto;
    width: 30%;
  }
</style>
