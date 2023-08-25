---
title: "LabelSprite"
draft: false
weight: 9
---

**LabelSprite** -- класс, описывающий 2D текст на сцене. Расширяет [THREE.Sprite](https://threejs.org/docs/index.html?q=Sprite#api/en/objects/Sprite).

```js
export class LabelSprite extends THREE.Sprite {
   constructor(parameters: LabelSpriteParameters);

  get sizeAttenuation(): boolean;
  set sizeAttenuation(value: boolean);

  get text(): string;
  set text(value: string);

  get fontFace(): string | FontFace;
  set fontFace(value: string | FontFace);

  get fontSize(): number;
  set fontSize(value: number);

  get borderThickness(): number;
  set borderThickness(value: number);

  get borderColor(): Color;
  set borderColor(value: Color);

  get borderRadius(): number;
  set borderRadius(value: number);

  get backgroundColor(): Color;
  set backgroundColor(value: Color);

  get textColor(): Color;
  set textColor(value: Color);

  get textPadding(): THREE.Vector4Tuple;
  set textPadding(value: THREE.Vector4Tuple);

  dispose(): void;
}
```

## Конструктор
```js
  constructor(parameters: LabelSpriteParameters);
```
где:\
`parameters`-- параметры текстовой метки. Подробнее: [LabelSpriteParameters](#LabelSpriteParameters).

## Свойства

###  sizeAttenuation: boolean
Задает или возвращает значение флага, показывающего влияние перспективы на текстовую метку - уменьшается ли размер метки с глубиной кадра.
Влияет на отображение только с перспективной камерой.
```js
  get sizeAttenuation(): boolean;
  set sizeAttenuation(value: boolean);
```
По умолчанию: `false` - размер метки не зависит от перспективы.

###  text: string
Задает или возвращает строку отображаемого текста.
```js
  get text(): string;
  set text(value: string);
```
По умолчанию пустая строка.


###  fontFace: string | FontFace
Задает или возвращает параметры шрифта.
```js
  get fontFace(): string | FontFace;
  set fontFace(value: string | FontFace);
```
где:\
 `fontFace` -- строка задающая [font-family](https://developer.mozilla.org/en-US/docs/Web/CSS/font-family), или объект [FontFace](https://developer.mozilla.org/en-US/docs/Web/API/FontFace) описывающий параметры шрифта.\
По умолчанию: `Roboto, sans-serif`.


###  fontSize: number
Задает или возвращает размер отображаемого текста в пикселях.
```js
  get fontSize(): number;
  set fontSize(value: number);
```
По умолчанию: `12`.


###  borderThickness: number
Задает или возвращает толщину рамки метки в пикселях.
```js
  get borderThickness(): number;
  set borderThickness(value: number);
```
По умолчанию: `2`.

###  borderColor: Color
Задает или возвращает цвет рамки метки.
```js
  get borderColor(): Color;
  set borderColor(value: Color);
```
По умолчанию: `Color(0, 0, 0, 1.0)`. Подробнее: [Color](../Color).

###  borderRadius: number
Задает или возвращает радиус скругления рамки метки в пикселях.
```js
  get borderRadius(): number;
  set borderRadius(value: number);
```
По умолчанию: `1`.

###  backgroundColor: Color
Задает или возвращает цвет фона метки.
```js
  get backgroundColor(): Color;
  set backgroundColor(value: Color);
```
По умолчанию: `Color(1.0, 1.0, 1.0, 1.0)`. Подробнее: [Color](../Color).


###  textColor: Color
Задает или возвращает цвет отображаемого текста.
```js
  get textColor(): Color;
  set textColor(value: Color);
```
По умолчанию: `Color(0, 0, 0, 1.0)`. Подробнее: [Color](../Color).

###  textPadding: THREE.Vector4Tuple
Задает или возвращает отступ текста от границ метки. Отступ задается в пикселях по порядку: слева, сверху, справа, снизу.
```js
  get textPadding(): THREE.Vector4Tuple;
  set textPadding(value: THREE.Vector4Tuple);
```
По умолчанию: `[0, 0, 0, 0]`.

## Методы

### dispose()
Метод освобождает ресурсы, выделенные `LabelSprite`.
```js
dispose(): void;
```


## LabelSpriteParameters {#LabelSpriteParameters}
Параметры текстовой метки. Задают соответствующие свойства `LabelSprite`.
```js
export interface LabelSpriteParameters {
  text?: string | undefined;
  sizeAttenuation?: boolean | undefined;
  fontFace?: string | FontFace | undefined;
  fontSize?: number | undefined;
  borderColor?: Color | undefined;
  backgroundColor?: Color | undefined;
  borderThickness?: number | undefined;
  borderRadius?: number | undefined;
  textColor?: Color | undefined;
  textPadding?: THREE.Vector4Tuple | undefined;
}
```