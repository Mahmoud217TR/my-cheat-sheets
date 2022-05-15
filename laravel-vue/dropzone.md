# Dropzone

**Table of Contents:**
* [Installation](#installation)
* [Setup](#setup)

## Installation

To Install Dropzone package `npm install --save dropzone`.



## Setup

This is a Setup example for dropzone:

```vue
<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <div class="dropzone-area d-flex justify-content-center bg-dark" ref="imageUpload">
                    <div class="drop-message py-2 text-center h2">
                        Drop your files Here
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { Dropzone } from 'dropzone';
export default {
    props: ['url'],
    data() {
        return {
            dropzone: null,
        }
    },
    mounted() {
        this.dropzone= new Dropzone(this.$refs.imageUpload,{
            url: this.url
        });
    },
}
</script>
```