<template>

</template>

<script>
  export default {
    props: {
      numInputs: {
        type: number,
        required: true
      },
      seperator: {
        type: Object,
        required: true
      },
      onChange: {
        type: Function,
        required: false
      }
    }
  };
</script>
