# SCSS STUDY 👨🏻‍🏫

## 주석 ✍🏻

// <== 이 주석은 SCSS => CSS로 compile할 때 compiled된 css file에서 보이지 않음. <br/>
/\*\*/ <== 이 주석은 위와 반대로 compile할 때
compiled된 css file에서 주석처리 된 형태로 확인 가능

<br/><br/>

## 변수 ✍🏻

$variable <= 달러 표시를 붙여주면 사용 가능하다. <br/>

```scss
$color: blue;

.container {
  h1 {
    color: $color;
  }
}
```

> js의 변수와도 같이 scss의 변수도 <span style="color:yellow">유효범위</span>를 가지고 있다.
> <br>위의 코드의 `$color`(변수)는 전역 변수이고, 아래의 코드에서는 `.container`안에서만 작동하는 변수이다.

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

## 자식 선택자 ✍🏻

`>` 를 사용하면 자식 선택자로 사용 가능하다.

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

## 상위 선택자 참조 ✍🏻

`&` 를 사용하여 표현할 수 있다.

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

위의 코드를 complied 된 css file로 확인하면

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

의 css 코드처럼 자신이 포함된 상위 선택자를 참조하고, <br/> 아래의 코드와 같이 편리하게 사용 할 수도 있다.

```SCSS
.fs {
  &-small { font-size: 10px;};
  &-medium { font-size: 10px;};
  &-large { font-size: 10px;}
}
```

<br/><br/>

## 중첩된 속성 ✍🏻

네임스페이스인 선택자들을 중첩시켜 더 편리하게 사용 할 수 있다.

> **_주의❗❗_**<br/>_선택자 처럼 사용을 하되_, 뒷부분에 <span style="color:yellow">`:`(콜론기호)</span>를 붙여주고, <span style="color:yellow">`{}`(중괄호)</span>가 끝나는 지점에 <span style="color:yellow">`;`(세미콜론)</span>을 붙여줘야 한다.

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

그리고 위의 코드를 compiled 된 css file로 확인하면 아래의 코드이다.

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

## 연산자 ✍🏻

> SCSS의 연산자는 다른 언어의 연산과 동일하지만,
> **_/(나누기)연산자_**를 쓰면 적용되지 않는다.
> 그 이유는 font는 단축 속성을 아래의 코드처럼 사용할 수 있다.

```scss
span {
  font-size: 10px;
  line-height: 10px;
  font-family: serif;
  font: 10px / 10px serif; // font-size / line-height font-family
}
```

font 단축 속성은 size, line-height, font-family까지 속성을 부여 해 줘야지 사용이 가능해서 잘 사용하지 않는다.

### 나누기 연산자 사용 방법 ❗❗

```scss
// 1. 중괄호를 사용한다.
margin: (30px / 2);

// 2. 변수사용.
$size: 30px;
margin: $size / 2;

// 3. 다른 연산자와 같이 사용한다.
margin: 10px + 12px / 2;
```

### 다른 단위의 연산 ❗❗

아래와 같은 단위가 다른 값은 연산을 할 수 없다... <br>그러면 어떻게 해야 할까 🤷🏻‍♂️

```scss
div {
  width: 100% - 200px;
}
```

**_`calc()` 함수를 사용하면 된다!!_**

```scss
div {
  width: calc(100% - 200px);
}
```
