<script lang="ts">
import { defineComponent } from "vue";
import CKEditor from '@ckeditor/ckeditor5-vue';
import ClassicEditor from '@ckeditor/ckeditor5-build-classic';

export default /*#__PURE__*/ defineComponent({
  name: "SmartTaskComponent", // vue component name
  components: { CKEditor, ClassicEditor },
  props: ['componentState', 'componentStatus'],
  data() {
    return { 
         editor: ClassicEditor,
                editorData: '<p>Content of the editor.</p>',
                editorConfig: {
                    // The configuration of the editor.
                },
      model: {
      content:""
    } };
  },
  computed: {},
  methods: {
    async submitForm() {
      this.$emit("execute-smart-task", this.model);
    },
  },
  created() {
    if (this.componentState) {
      this.model = this.componentState;
    }
  },
  setup() {},
});
</script>

<template>
 <div style="font-family: Avenir, sans-serif">
  <CKEditor style="height:500px" :editor="editor" v-model="editorData" :config="editorConfig"></CKEditor>
  </div>
 
</template>

