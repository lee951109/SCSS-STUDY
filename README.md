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

<br/><br/>

## 자식 선택자 ✍🏻

"`>`" 를 사용하면 자식 선택자로 사용 가능하다.

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

"`&`" 를 사용하여 표현할 수 있다.

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
