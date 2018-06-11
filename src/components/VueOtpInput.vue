<template>
  <div class="div__style">
    <span v-for="i in numInputs" :key="i">
      <div class="sep">
        <input :class="inputStyle ? '' : 'inputStyling'" :disabled="disable" :style="inputStyle" type="tel" maxLength="1" ref="input" />
        <span v-show="i < numInputs">{{seperator}}</span>
      </div>
    </span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        activeInput: ''
      };
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
      disabled: {
        type: Boolean,
        required: false
      },
      onChange: {
        type: Function,
        required: false
      },
      disable: {
        type: Boolean,
        required: false
      },
      shouldAutoFocus: {
        type: Boolean,
        required: false
      }
    },
    methods: {
      focusInput(input) {
        const { numInputs } = this;
        this.activeInput = Math.max(Math.min(numInputs - 1, input), 0);
      },
      focusNextInput() {
        const { activeInput } = this;
        this.focusInput(activeInput + 1);
      },
      focusPrevInput() {
        const { activeInput } = this;
        this.focusInput(activeInput - 1);
      }
    },
    mounted: function() {
      const { shouldAutoFocus } = this;
      if (shouldAutoFocus) {
        this.$refs.input[0].focus();
      }
    }
  };
</script>

<style>
  .inputStyling {
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
