<template>
  <div class="app-container">
    <tinymce-editor
      ref="editor"
      v-model="content"
      :disabled="false"
      style="width:100%"
    />
  </div>
</template>

<script>
import TinymceEditor from '../../components/tinymce/tinymce'
export default {
  components: {
    TinymceEditor
  },
  data() {
    return {
      content: ''
    }
  },
  methods: {
    submit() {
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
