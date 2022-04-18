# CKEditor with Laravel-Vue

**Table of Contents:**
* [Installation](#installation)
* [Toolbar](#toolbar)


## Installation

To install CKEditor on laravel-vue project follow these steps:

* Install ckeditor pakage `npm install --save @ckeditor/ckeditor5-vue @ckeditor/ckeditor5-build-classic`.

* Import CKEditor in `app.js` file:

```javaScript
import CKEditor from '@ckeditor/ckeditor5-vue';

let app=createApp({}).use(CKEditor)
```

* Make an Editor component:

```vue
<template>
    <ckeditor :editor="editor" v-model="editorData"  tag-name="textarea" :id='inputId' :name='inputName' :config="editorConfig">
    </ckeditor>
</template>

<script>
import ClassicEditor from '@ckeditor/ckeditor5-build-classic';
    export default {
        props: ['data','input-id','input-name'],
        data() {
            return {
                editor: ClassicEditor,
                editorData: this.data,
                editorConfig: {
                    // for Editor's config
                }
            }
        }
    }
</script>
```


## Toolbar

To edit toolbar in the component file in the `editorConfig` field as follows:

```vue
<template>
    <ckeditor :editor="editor" v-model="editorData"  tag-name="textarea" :id='inputId' :name='inputName' :config="editorConfig">
    </ckeditor>
</template>

<script>
import ClassicEditor from '@ckeditor/ckeditor5-build-classic';
    export default {
        props: ['data','input-id','input-name'],
        data() {
            return {
                editor: ClassicEditor,
                editorData: this.data,
                editorConfig: {
                    toolbar: {
                        items: [
                            'heading', '|',
                            'bold', 'italic', '|',
                            'link', '|',
                            'outdent', 'indent', '|',
                            'bulletedList', 'numberedList', '|',
                            'insertTable', '|',
                            'mediaEmbed', 'blockQuote', '|',
                            'undo', 'redo'
                        ],
                        shouldNotGroupWhenFull: true
                    },
                }
            }
        }
    }
</script>
```