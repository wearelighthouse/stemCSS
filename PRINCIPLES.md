# Principles
1. **Don't repeat, or unset styles**
2. **Code 'mess' has to live somewhere**
<br><br><br>
## 1. Don't repeat, or unset styles  
stemCSS achieves this by:  
### Build classes that are specific and explicit
  - If a `color: black` is only applied on `:hover` at breakpoint `large`, your class is `.u-color-black@hover@large`
  - Which in your compiled css would be:
  ```
    @media (min-width: 1240px) {
      .u-color-black\@hover\@large {
        color: black;
      }
    }
  ```
### Too edge-case? Keep it tied to a component until you re-use it
```
.c-form {
  &__label {
    @include breakpoint(large) {
      &:hover {
        color: $colour-black;
      }
    }
  }
}
```

<br>

### `@extend` to apply each `property: value` to an Object or Component
  - The codebase creates `.u-color-black` as a Utility
  - Five components want to use `color: black;`
  - `.c-button { @extend .u-color-black; } `
  - Compiled CSS: `.u-color-black, .c-button { color: black; }`

<br>

## 2. Code 'mess' has to live somewhere
You can build up and style your components in your **HTML**, or in your **SCSS**. This is where your mess will live.

<br>

### Option A - Mess in the HTML

```
<a class="u-flex u-ai-center u-jc-center u-bgcolor-green u-shadow u-h4 u-weight-bold u-family-roboto">Submit</a>
```

<br>

### Option B - Mess in the SCSS
```
 .c-submit {
   @extend .u-flex;
   @extend .u-ai-center;
   @extend .u-jc-center;
   @extend .u-bgcolor-green;
   @extend .u-shadow;
   @extend .u-h4;
   @extend .u-weight-bold;
   @extend .u-family-roboto;
 }
```

<br>

### Option C - A bit of both
```
 <a class="c-submit u-bgcolor-green u-shadow">Submit</a>
 
 .c-submit {
   @extend .u-flex;
   @extend .u-ai-center;
   @extend .u-jc-center;
   @extend .u-h4;
   @extend .u-weight-bold;
   @extend .u-family-roboto;
 }
```

### The decision is just 'where do  I prefer to manage these 'sets' of classes?
