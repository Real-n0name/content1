🛠 Очень частый кейс — сделать полупрозрачную заливку поверх картинки. Это обычно называют оверлеем или вуалью. В этом случае не стоит применять свойство `opacity`, работайте с полупрозрачными цветами с альфа-каналом.

Например, так:

```css
selector {
  position: relative;
}

selector:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgb(0 0 0 / 0.5);
  /* или в формате HEX
  background-color: #00000080; */
}
```

🛠 Когда-то была популярна шутка, что если ваш заказчик не заплатил вам, то его можно шантажировать следующим способом: цепляете на сайт скрипт, который будет каждый день уменьшать `opacity` для `body` на 0.1 пока сайт полностью не пропадёт или пока заказчик не заплатит 😬

Если что, это не я вам рассказала 🤫
