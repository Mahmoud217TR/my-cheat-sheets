# CSS Tips & Tricks

**Table of Content:**
* [Text Truncate](#text-truncate)
* [Importing svg as object](#importing-svg-as-object)


## Text Truncate

To Truncate a text after 3 lines:

```css
.truncate-3-lines{
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
    -moz-box-orient: vertical;
    -ms-box-orient: vertical;
    overflow: hidden;
}
```

Another Way:

```css
.line-truncate{
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -moz-box-orient: vertical;
  -ms-box-orient: vertical;
  overflow: hidden;
}

.line-of-2{
    -webkit-line-clamp: 2;
}

.line-of-3{
    -webkit-line-clamp: 3;
}
```

## Importing svg as object

Assume we have an svg `happy.svg` and we want to import it as object:

```html
<object data="happy.svg" width="300" height="300"> </object>
```
