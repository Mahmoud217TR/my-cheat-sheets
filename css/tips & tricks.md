# CSS Tips & Tricks

**Table of Content:**
* [Text Truncate](#text-truncate)


## Text Truncate

To Truncate a text after 3 lines:

```css
.truncate-3-lines{
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    overflow: hidden;
}
```