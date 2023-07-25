---
title: "Color"
draft: false
weight: 9
---

**Color** -- класс, описывающий цвет [ViewObject](../ViewObject).

```js
export class Color {
  constructor(public r: number, public g: number, public b: number, public a: number);

  static fromThreeColor(color: THREE.Color, alpha = 1.0): Color;

  static fromColorRepresentation(representation: THREE.ColorRepresentation): Color;

  static fromMaterial(material: THREE.Material): Color;

  threeColor(): THREE.Color;

  alpha(): number;

  fromArray(array: ArrayLike<number>, offset = 0): Color {
    this.r = array[offset];
    this.g = array[offset + 1];
    this.b = array[offset + 2];
    this.a = array[offset + 3];
    return this;
  }

  toArray(array: Array<number>, offset = 0): Array<number> {
    array[offset] = this.r;
    array[offset + 1] = this.g;
    array[offset + 2] = this.b;
    array[offset + 3] = this.a;
    return array;
  }
}
```
## Конструктор
```js
  constructor(r: number, g: number, b: number, a: number);
```
где:\
`r` -- значение интенсивности красной компоненты цвета, от `0.0` до `1.0`.\
`g` -- значение интенсивности зелёной компоненты цвета, от `0.0` до `1.0`.\
`b` -- значение интенсивности синей компоненты цвета, от `0.0` до `1.0`.\
`a` -- альфа канал, значение прозрачности, от `0.0` до `1.0`.

## Методы

### fromThreeColor()
Метод возвращает объект `Color` с `r`, `g`, `b` - компонентами цвета, соответствующими `r`, `g`, `b` - компонентам параметра `color` и прозрачностью равной `alpha`.
```js
  static fromThreeColor(color: THREE.Color, alpha = 1.0): Color;
```
где:
`color` - источник `r`, `g`, `b` компонент цвета. Подробнее: [THREE.Color](https://threejs.org/docs/#api/en/math/Color).\
`alpha` - значение прозрачности, от `0.0` до `1.0`. По умолчанию `1.0`.

### fromColorRepresentation()
Метод возвращает объект `Color` с параметрами цвета, соответствующими `THREE.ColorRepresentation` и прозрачностью равной `1.0`.
```js
  static fromColorRepresentation(representation: THREE.ColorRepresentation): Color;
```
где:
`THREE.ColorRepresentation` - объект представления цвета в виде `THREE.Color | string | number`. Подробнее: [THREE.Color](https://threejs.org/docs/#api/en/math/Color)

### fromMaterial()
Метод возвращает объект `Color` с параметрами цвета, соответствующими `material`.
```js
  static fromMaterial(material: THREE.Material): Color;
```
где:
`material` - материал, по которому вычисляются параметры цвета.\
 `r`, `g`, `b` - компоненты цвета берутся равнымим `r`, `g`, `b` - компонентам свойства `color`, если материал определяет это свойство (пример: [MeshBasicMaterial.color](https://threejs.org/docs/#api/en/materials/MeshBasicMaterial.color)). Если нет, то берутся значения по умолчанию: `1.0`.\
 `alpha` - значение прозрачности берётся равным значению свойства [Material.opacity](https://threejs.org/docs/#api/en/materials/Material.opacity).

### threeColor()
Метод возвращает объект [THREE.Color](https://threejs.org/docs/#api/en/math/Color) с параметрами цвета, соответствующими текущему `Color`.
```js
  threeColor(): THREE.Color;
```

### alpha()
Метод возвращает значение прозрачности.
```js
  alpha(): number;
```