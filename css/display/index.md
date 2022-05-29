---
title: "`display`"
description: "Как поставить несколько элементов `<div>` в строку? Объясняем, как менять стандартный тип отображения на произвольный. Подробно говорим об основных типах отображения."
authors:
  - solarrust
contributors:
  - skorobaeus
editors:
  - tachisis
keywords:
  - блочная модель
  - block
  - inline-block
  - flex
  - grid
tags:
  - doka
---

## Кратко

По умолчанию все элементы в HTML бывают блочными и строчными. Но в вёрстке часто бывает, что нам нужно сделать элемент не строчным, а блочным. И наоборот.

Тут на помощь приходит свойство `display` ✨

Помимо значений `block` (блочное отображение) и `inline` (строчное отображение) существует смешанное значение `inline-block` (строчно-блочное отображение).

Бывают и другие специфичные значения, например, `flex`, `grid`, `table-cell`.

## Пример

Частая ситуация: на странице нужно показать иконки соцсетей со ссылками на аккаунты.

```html
<div class="wrapper">
  <ul class="social">
    <li class="social__item twitter">
      <a href="" class="social__link"></a>
    </li>
    <li class="social__item fb">
      <a href="" class="social__link"></a>
    </li>
    <li class="social__item youtube">
      <a href="" class="social__link"></a>
    </li>
  </ul>
</div>
```

Обратите внимание, что внутри ссылок ничего не написано. Нам не нужно выводить название соцсети, а нужно вывести иконку с логотипом. Что мы и сделаем при помощи фона.

Выстраиваем пункты списка в ряд, а не друг под другом:

```css
.social__item {
  display: inline-block;
}
```

Превращаем ссылки из строчных в блочные элементы. После этого можем задать высоту и ширину:

```css
.social__link {
  display: block;
  width: 30px;
  height: 30px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
}
```

Задаём иконки фоном для каждой отдельной ссылки:

```css
.twitter {
  background-image: url(twitter-round-blue.png);
}

.fb {
  background-image: url(fb-square-blue.png);
}

.youtube {
  background-image: url(youtube-red-square.png);
}
```

По умолчанию ссылки — строчные. Это значит, что им нельзя задать размеры (ширину и высоту) и фоновую картинку.

Пишем `display: block`, и строка превращается в условный _прямоугольник_, у которого могут быть и размеры, и фон.

После этого смело меняем размер на нужный нам и фоном выводим иконки каждой из соцсетей.

Помимо этого по ходу решения задачи мы установили свойство `display: inline-block` для пунктов списка с классом `.social__item`. За счёт этого элементы, которые по умолчанию блочные, приобретают внешние признаки строчных элементов. Вместо того чтобы выстраиваться друг под другом, пункты списка теперь стоят рядом, в строку.

## Как понять

Каждый HTML-элемент по умолчанию имеет свой тип отображения. Например, ссылки нужны для оборачивания слов и фраз. Значит, они должны быть строчными, чтобы не разорвать окружающий текст.

Но по разным причинам может понадобиться изменить стандартное отображение на то, что больше подходит под решение текущей задачи.

## Как пишется

Пишем имя свойства `display` и после двоеточия через пробел указываем одно из доступных значений при помощи ключевого слова.

Значения свойства, которые встречаются в работе чаще всего:

- `none` — полностью скрывает элемент со страницы, не удаляя его при этом из HTML-разметки.
- `block` — элемент ведёт себя как блочный.
- `inline-block` — элемент ведёт себя снаружи как строчный, а внутри как блочный.
- `flex` — элемент становится флекс-контейнером, ведёт себя как блочный, а вложенные элементы становятся флекс-элементами. Подробнее в [Гайде по flexbox](/css/flexbox-guide/).
- `grid` — элемент становится грид-контейнером. Снаружи грид-контейнер ведёт себя как блок. Дочерние элементы такого контейнера начинают подчиняться правилам грид-раскладки. Подробнее в [Гайде по grid](/css/grid-guide/).

Остальные значения можно посмотреть в [спецификации](https://www.w3.org/TR/css-display-3/#the-display-properties).

Это свойство можно применить к любому HTML-элементу.

## Подсказки

💡 Свойство `display` нельзя анимировать 😔

💡 Значение по умолчанию у каждого HTML-элемента своё. Если нет уверенности — загляните в «Инструменты разработчика» в браузере.