---
title: "ModelElementPropertyValue"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 5
---

**ModelElementPropertyValue** -- этот класс описывает значение свойства элемента модели.

```js
class ModelElementPropertyValue {
  str_value?: string;
  int_value?: number;
  double_value?: number;
  date_value?: BigInt;
  array_value: Array<string>;
  decimal_value?: number;
  guid_value?: string;
  array_int_value: Array<number>;
  bool_value?: boolean;
  get value(): any;
}
```

{{< hint type="important" icon=gdoc_error_outline title="Важно" >}}
Заполнено будет только одно поле, соответствующее типу значения этого свойства.
Например: если значение равно `0.0`, то будет заполнено поле `double_value`.
{{< /hint >}}

