---
title: "Тернарный оператор"
description: "Что такое тернарный оператор и как он заменяет короткие if"
authors:
  - gingerraccoon
keywords:
  - тернарный
  - условный
  - оператор
tags:
  - doka
---

## Кратко

Тернарный оператор позволяет записать условие и выражения очень компактно, в одну строку.

## Как пишется

```js
(A) ? (B) : (C)
```

Где A — условие, B — первое выражение, C — второе выражение.

Если первый операнд A вычисляется в истинное выражение (`true`), то оператор вернёт выражение B, если в `false` — вернёт выражение C.

## Как понять

По механике работы оператор похож на инструкцию [`if...else`](/js/if-else), но позволяет писать меньше кода или записать результат сравнения в переменную. Например:

```js
const num = 10
let result

if (num > 10) {
  result = 'Число больше 10'
} else {
  result = 'Число меньше или равно 10'
}

console.log(result)
```

Можно заменить тернарным оператором и сократить код:

```js
const num = 10

const result = num > 10 ? 'Число больше 10' : 'Число меньше или равно 10'

console.log (result)
```

Обратите внимание, во втором примере мы уже используем `const` вместо `let`, потому что переприсвоения значения переменной уже нет.

## Вариации

Результат возвращаемый тернарным оператором можно записать в переменную (как в примере выше) или вернуть с помощью `return` внутри функции:

```js
const salutation = function(name) {
  return name ? `Рад видеть, ${name}!` : 'Привет, друг!'
}

salutation('Дока Дог')
// 'Рад видеть, Дока Дог!'
salutation()
// 'Привет, друг!'
```

<aside>

  💡 Раз результат работы тернарного оператора можно записать в переменную, то смело делаем вывод, тернарный оператор - выражение. Подробнее можно прочитать [тут](/js/expressions-vs-statements)

</aside>

Так же поддерживается вложенность нескольких условий:

```js
const num = 10

const result = num > 10 ? 'Число больше 10' : num === 10 ? 'Число равно 10' : 'Число меньше 10'

console.log(result) // 'Число равно 10'
```
В данном примере сначала будет проверяться второе условие `num === 10 ? 'Число равно 10' : 'Число меньше 10'`. В случае если `num !=== 10` результатом вычисления станет `'Число меньше 10'` и первое условие приобритет вид `num > 10 ? 'Число больше 10' : 'Число меньше 10'`

<details>
  <summary>Ассоциативность справа</summary>
  Ассоциативность - порядок обработки операторов с одинаковым приоритетом.
  Тернарный оператор имеет ассоциативность справа налево, так же как и оператор присваивания. Например данные выражения - одинаковы:

  ```js
  a = b = c = d
  a = (b = (c = d))
  ```

</details>

## Что выбрать?

При выборе между [`if...else`](/js/if-else) и тернарным оператором в приоритет нужно ставить читабельность. Чем код нагляднее и понятнее, тем проще с ним в дальнейшем работать.