---
title: "Color"
draft: false
weight: 9
---

**Color** -- класс, описывающий цвет [ViewObject](../ViewObject).

```js
export class Color {
  constructor(public r: number, public g: number, public b: number, public a: number);

  static fromThreeColor(color: THREE.Color, alpha = 1): Color;

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
