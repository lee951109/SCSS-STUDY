# SCSS STUDY π¨π»βπ«

## μ£Όμ βπ»

// <== μ΄ μ£Όμμ SCSS => CSSλ‘ compileν  λ compiledλ css fileμμ λ³΄μ΄μ§ μμ. <br/>
/\*\*/ <== μ΄ μ£Όμμ μμ λ°λλ‘ compileν  λ
compiledλ css fileμμ μ£Όμμ²λ¦¬ λ ννλ‘ νμΈ κ°λ₯

<br/><br/>

## λ³μ βπ»

$variable <= λ¬λ¬ νμλ₯Ό λΆμ¬μ£Όλ©΄ μ¬μ© κ°λ₯νλ€. <br/>

```scss
$color: blue;

.container {
  h1 {
    color: $color;
  }
}
```

> jsμ λ³μμλ κ°μ΄ scssμ λ³μλ <span style="color:yellow">μ ν¨λ²μ</span>λ₯Ό κ°μ§κ³  μλ€.
> <br>μμ μ½λμ `$color`(λ³μ)λ μ μ­ λ³μμ΄κ³ , μλμ μ½λμμλ `.container`μμμλ§ μλνλ λ³μμ΄λ€.

```scss
.container {
  $color: blue;
  h1 {
    color: $color;
  }

.box {
  h1{
    color : $color; // error
  }
}
```

<br/><br/>

## μμ μ νμ βπ»

`>` λ₯Ό μ¬μ©νλ©΄ μμ μ νμλ‘ μ¬μ© κ°λ₯νλ€.

```scss
.container {
  > ul {
    li {
      font-size: 40px;
      .name {
        color: royalblue;
      }
      .age {
        color: rosybrown;
      }
    } // li
  } // ul
} // container
```

<br/><br/>

## μμ μ νμ μ°Έμ‘° βπ»

`&` λ₯Ό μ¬μ©νμ¬ ννν  μ μλ€.

```scss
.btn {
  position: absolute;
  &.active {
    color: red;
  }
}

.list {
  li {
    &:last-child {
      margin-left: 0;
    }
  }
}
```

μμ μ½λλ₯Ό complied λ css fileλ‘ νμΈνλ©΄

```css
.btn {
  position: absolute;
}
.btn.active {
  color: red;
}

.list li:last-child {
  margin-left: 0;
}
```

μ css μ½λμ²λΌ μμ μ΄ ν¬ν¨λ μμ μ νμλ₯Ό μ°Έμ‘°νκ³ , <br/> μλμ μ½λμ κ°μ΄ νΈλ¦¬νκ² μ¬μ© ν  μλ μλ€.

```SCSS
.fs {
  &-small { font-size: 10px;};
  &-medium { font-size: 10px;};
  &-large { font-size: 10px;}
}
```

<br/><br/>

## μ€μ²©λ μμ± βπ»

λ€μμ€νμ΄μ€μΈ μ νμλ€μ μ€μ²©μμΌ λ νΈλ¦¬νκ² μ¬μ© ν  μ μλ€.

> **_μ£Όμββ_**<br/>_μ νμ μ²λΌ μ¬μ©μ νλ_, λ·λΆλΆμ <span style="color:yellow">`:`(μ½λ‘ κΈ°νΈ)</span>λ₯Ό λΆμ¬μ£Όκ³ , <span style="color:yellow">`{}`(μ€κ΄νΈ)</span>κ° λλλ μ§μ μ <span style="color:yellow">`;`(μΈλ―Έμ½λ‘ )</span>μ λΆμ¬μ€μΌ νλ€.

```SCSS
.box {
  font: {
    weight: bold;
    size: 10px;
    family: sans-serif;
  };
  margin: {
    top: 10px;
    left: 20px;
  };
  padding: {
    top: 10px;
    bottom: 40px;
    left: 20px;
    right: 30px;
  };
```

κ·Έλ¦¬κ³  μμ μ½λλ₯Ό compiled λ css fileλ‘ νμΈνλ©΄ μλμ μ½λμ΄λ€.

```CSS
.box{
  font-weight: bold;
  font-size: 10px;
  font-family: sans-serif;
  margin-top: 10px;
  margin-left: 20px;
  padding-top: 10px;
  padding-bottom: 40px;
  padding-left: 20px;
  padding-right: 30px;
}
```

<br/><br/>

## μ°μ°μ βπ»

> SCSSμ μ°μ°μλ λ€λ₯Έ μΈμ΄μ μ°μ°κ³Ό λμΌνμ§λ§,
> **_/(λλκΈ°)μ°μ°μ_**λ₯Ό μ°λ©΄ μ μ©λμ§ μλλ€.
> κ·Έ μ΄μ λ fontλ λ¨μΆ μμ±μ μλμ μ½λμ²λΌ μ¬μ©ν  μ μλ€.

```scss
span {
  font-size: 10px;
  line-height: 10px;
  font-family: serif;
  font: 10px / 10px serif; // font-size / line-height font-family
}
```

font λ¨μΆ μμ±μ size, line-height, font-familyκΉμ§ μμ±μ λΆμ¬ ν΄ μ€μΌμ§ μ¬μ©μ΄ κ°λ₯ν΄μ μ μ¬μ©νμ§ μλλ€.

### λλκΈ° μ°μ°μ μ¬μ© λ°©λ² ββ

```scss
// 1. μ€κ΄νΈλ₯Ό μ¬μ©νλ€.
margin: (30px / 2);

// 2. λ³μμ¬μ©.
$size: 30px;
margin: $size / 2;

// 3. λ€λ₯Έ μ°μ°μμ κ°μ΄ μ¬μ©νλ€.
margin: 10px + 12px / 2;
```

### λ€λ₯Έ λ¨μμ μ°μ° ββ

μλμ κ°μ λ¨μκ° λ€λ₯Έ κ°μ μ°μ°μ ν  μ μλ€... <br>κ·Έλ¬λ©΄ μ΄λ»κ² ν΄μΌ ν κΉ π€·π»ββοΈ

```scss
div {
  width: 100% - 200px;
}
```

**_`calc()` ν¨μλ₯Ό μ¬μ©νλ©΄ λλ€!!_**

```scss
div {
  width: calc(100% - 200px);
}
```

<br/><br/>

## SCSSμ μ¬νμ©(Mixins) βπ»

cssλ₯Ό μ¬μ©νλ€ λ³΄λ©΄ μλμ μ½λμ²λΌ μ€λ³΅λλ λΆλΆμ΄ λλ¬΄ λ§μ΄ μλ€. <br/>

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}
.container .item {
  display: flex;
  justify-content: center;
  align-items: center;
}
.box {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

μ΄λ¬ν λΆλΆμ μλμ SCSS μμ `@Mixin` ν€μλλ₯Ό μ¬μ©νμ¬ μ¬νμ© μ½λλ₯Ό λ§λ€μ΄ μ£Όκ³  `@include` ν€μλλ₯Ό μ¬μ©ν΄μ μ¬μ¬μ© νλ©΄ μ‘°κΈ λ μ½κ² μ¬μ© ν  μ μλ€.

```scss
@mixin center {
  // κ³΅ν΅μΌλ‘ μ¬μ©νλ λΆλΆμ @mixinμΌλ‘ λ§λ€μ΄ μ€λ€.
  display: flex;
  justify-content: center;
  align-items: center;
}
.container {
  @include center; // μ¬μ©ν  λ, @includeλ₯Ό μ¬μ©ν΄μΌ νλ€.
  .item {
    @include center;
  }
}
.box {
  @include center;
}
```

νμ§λ§ββ λ§μ½ μλμ μ½λμμ `.item`μ `width, height`μ κ°μ 100pxμ΄ μλ 200pxλ‘ λ³κ²½νκ³  μΆμ λ, <span style="color:yellow">@mixin </span>λ₯Ό μ¬μ©ν  μ μμκΉ..?

```scss
@mixin box {
  width: 100px;
  height: 100px;
  background-color: green;
}
.container {
  @include box;
  .item {
    @include box;
  }
}
.box {
  @include box;
}
```

javascript μμ μ¬μ© νλ―μ΄ μλμ²λΌ <span style="color:yellow">ν¨μ($λ§€κ°λ³μ)</span>λ₯Ό μ¬μ©νλ©΄ μ½κ² κ°μ λ°κΏμ€ μ μλ€.

```scss
@mixin box($size: 100px, $color: green) {
  // :λ€μ κ°μ μΈμκ° μλ€λ©΄ κΈ°λ³Έκ°μΌλ‘ μ¬μ©ν  κ°μ΄λ€.
  width: $size;
  height: $size;
  background-color: $color;
}
.container {
  @include box(200px, blue);
  .item {
    @include box(
      $color: yellow
    ); // keyword μΈμ => λ§€κ°λ³μμ λ°λ‘ λλ €λ°λ λ°©λ².
  }
}
.box {
  @include box;
}
```

<br/><br/>

## λ°λ³΅λ¬Έ βπ»

μ΄λ μΈμ΄λ₯Ό λ°°μ°λλΌλ λ°λ³΅λ¬Έμ κΈ°μ΄μ€μ κΈ°μ΄λ‘ λ°°μΈ μ μκ³ , μ΄λ¬ν λ°λ³΅λ¬Έμ SCSSμμλ μ¬μ© κ°λ₯νλ€.

JSμ λΉκ΅νλ©΄μ λ³΄λ©΄ μ½κ² κ΅¬λΆ κ°λ₯ ν  κ²μ΄λ€.

```js
// JS
for (let i = 0; i < 10; i++) {
  console.log(`loop-${i}`);
}
```

```scss
// SCSS
@for $i from 1 through 10 {
  .box:nth-chold(#{i}) {
    width: 100px;
    height: 100px * $i;
  }
```

<br/><br/>

## ν¨μ βπ»

JS, JAVAλ±μ μ¬μ© ν΄λ΄€λ€λ©΄ μΉμνκ² λκ»΄μ§ λ§ν μ½λμ΄λ€.

```SCSS
@function ratio($size, $ratio) {
  @return $size * $ratio
}
.box {
  $width : 100px;
  width: $width;
  height: ratio($width, 9 / 16);
}
```
