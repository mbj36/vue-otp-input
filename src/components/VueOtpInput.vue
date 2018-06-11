<template>
  <div class="div__style">
    <span v-for="i in numInputs" :key="i">
      <div class="sep">
        <input @keydown="handleKey" @change="handleChange" :class="inputStyle ? '' : 'inputStyling'" :disabled="disabled" :style="inputStyle" type="tel" maxLength="1" ref="input" />
        <span v-show="i < numInputs">
          <strong>{{seperator}}</strong>
        </span>
      </div>
    </span>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        activeInput: 0
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
      },
      handleKey(e) {
        switch (e.keyCode) {
          case 8:
            e.preventDefault();
            this.focusPrevInput(this.activeInput);
            break;
          case 46:
            e.preventDefault();
            break;
          case 37:
            e.preventDefault();
            this.focusPrevInput(this.activeInput);
            break;
          case 39:
            e.preventDefault();
            this.focusNextInput(this.activeInput);
            break;
          default:
            break;
        }
      },
      handleChange(e) {
        this.focusNextInput();
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
    font-size: 1em;
    padding: 2em;
    margin: 1em;
  }
  .div__style {
    display: flex;
  }
  .sep {
    display: flex;
  }
  .sep > span {
    margin-top: 40%;
  }
</style>
