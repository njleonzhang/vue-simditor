<template lang='pug'>
  .editor-wrapper
    textarea#editor
</template>

<script>
  import $ from 'jquery'
  import Simditor from 'simditor'
  import 'simditor/styles/simditor.css'

  export default {
    name: 'simditor',
    props: {
      content: {
        type: String,
        default: ''
      },
      options: {
        type: Object,
        default() {
          return {}
        }
      }
    },

    data() {
      return {
        editor: ''
      }
    },

    watch: {
      content(val) {
        this.editor.setValue(val)
      }
    },

    mounted() {
      /* eslint-disable no-new */
      console.log(Object.assign({}, {
        textarea: $('#editor')
      }, this.options))
      this.editor = new Simditor(Object.assign({}, {
        textarea: $('#editor')
      }, this.options))

      this.editor.on('valuechanged', (e, src) => {
        this.valueChange(e, src)
      })
    },

    methods: {
      valueChange(e, val) {
        this.$emit('change', this.editor.getValue())
      }
    }
  }
</script>
