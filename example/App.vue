<template lang='pug'>
  .vue-simditor
    simditor(
      :content='initContent',
      :options='options',
      @change='change')
</template>

<script>
import Simditor from '../src/index.js'

export default {
  components: {
    Simditor
  },

  data() {
    return {
      initContent: '',
      options: {
        placeHolder: 'this is placeHolder',
        toolbarFloat: false
      }
    }
  },

  methods: {
    change(val) {
      console.log(val)
    }
  }
}
</script>
