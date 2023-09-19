---
title: "IControl"
draft: false,
weight: 13
---

**IControl** - интерфейс, описывающий базовый элемент управления.

```js
export interface IControl {
  container: HTMLElement;
  getId(): string;
  setToolTip(tooltipText: string): void;
  setText(text: string): void;
}
```

## Свойства

### container
```js
container: HTMLElement;
```
DOM представление компонента.

## Методы

### getId()
Возвращает идентификатор элемента.
```js
getId(): void;
```

### setToolTip()
Устанавливает подсказку при наведении.
```js
setToolTip(tooltipText: string): void;
```
где:\
`tooltipText` - текст, который будет отображаться при наведении.


### setText()
Устанавливает текст элемента.
```js
setText(text: string): void;
```
где:\
`text` - текст, который будет отображаться в элементе.
