# Dropzone

**Table of Contents:**
* [Installation](#installation)
* [Setup](#setup)

## Installation

To Install Dropzone package `npm install --save dropzone`.



## Setup

* This is a Setup example for dropzone as a Vue Component if you are Usig **API Routes**:

```vue
<template>
    <div class="container">
        <div class="dropzone-area row justify-content-center" ref="imageUpload">
            <div class="drop-message col-12 py-2 text-center bg-dark h2">
                Drop your files Here
            </div>
        </div>
    </div>
</template>
<script>
import { Dropzone } from 'dropzone';
export default {
    props: ['url','method'],
    data() {
        return {
            dropzone: null,
        }
    },
    mounted() {
        this.dropzone= new Dropzone(this.$refs.imageUpload,{
            url: this.url,
            method: this.method,
        });
    },
}
</script>
```

* This is a Setup example for dropzone as a Vue Component if you are Usig **Web Routes**:

```vue
<template>
    <div class="container">
        <div class="dropzone-area row justify-content-center" ref="imageUpload">
            <div class="drop-message col-12 py-2 text-center bg-dark h2">
                Drop your files Here
            </div>
        </div>
    </div>
</template>
<script>
import { Dropzone } from 'dropzone';
export default {
    props: ['url','csrfToken','method'],
    data() {
        return {
            dropzone: null,
        }
    },
    mounted() {
        this.dropzone= new Dropzone(this.$refs.imageUpload,{
            url: this.url,
            headers: {
                    "X-CSRF-TOKEN": this.csrfToken
            },
            method: this.method,
        });
    },
}
</script>
```
> for easier config use the **API Routes** to avoid `CSRF token mismatch`.