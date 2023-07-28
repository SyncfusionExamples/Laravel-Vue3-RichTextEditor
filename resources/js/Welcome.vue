
<template>
    <div>
        <div class="control-section">
        <div class="sample-container">
            <div class="default-section">
            <div id="defaultRTE">
                <ejs-richtexteditor id="default" ref="rteInstance">
                <p>The Rich Text Editor component is a WYSIWYG ("what you see is what you get") editor that provides the best user experience to create and update the content. Users can format their content using standard toolbar commands.</p>
                </ejs-richtexteditor>
            </div>
            </div>
        </div>
        </div>
    </div>
</template>
<script>
import { RichTextEditorComponent, Toolbar, Link, Image, HtmlEditor, Table } from "@syncfusion/ej2-vue-richtexteditor";

export default {
  name: "App",
  components: {
    "ejs-richtexteditor": RichTextEditorComponent,
  },

  data: function () {
    return {};
  },
  methods: {},
  provide: {
    richtexteditor: [Toolbar, Link, Image, HtmlEditor, Table],
  },
};
</script>

