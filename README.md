# Utilities
Class that produces a single `value: property`.
```
.u-color-black { color: black; }
.u-flex { display: flex; }
.u-pos-absolute { position: absolute; }
```

_In some circumstances_ - like `mh` (`margin-left`, `margin-right`), a utility produces two properties.
```
.u-mh-auto {
  margin-left: auto;
  margin-right: auto;
}
```

# Objects
Layouts objects - grids, containers, and helpful sets of classes like aspect-ratio etc.  
Never *visual* - you can't picture an object because it has no colours. If it has _colours_ - it's _probably_ a component.  
Objects typically @extend utilities.
```
.o-container {
  @extend .u-mh-auto;
  width: 90vw;
}
```

# Components
*Visual components* in your design system. `Header, Button, Footer, Hero` etc.  
Follow the *BEM* methodology for their children _where appropriate_.  
```
.c-button {
  @extend .u-flex;
  @extend .u-bgcolor-black;
  @extend .u-color-white;

  &__icon {
    @extend .u-pos-absolute;
    @extend .u-left-50pc;
    transform: translateX(-50%);
  }
}
```
