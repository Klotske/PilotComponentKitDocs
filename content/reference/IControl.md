---
title: "IControl"
draft: false,
weight: 13
---

**IControl** - интерфейс ui элементов.

```js
export interface IControl {
  container: HTMLElement;
  getId: () => string;
  setToolTip?: (tooltipText: string) => void;
}
```

## Свойства

### container
```js
container: HTMLElement;
```
Элемент-контейнер контрола.

## Методы

### getId()
Возвращает идентификатор элемента.
```js
getId(): void;
```

### setToolTip()
Возвращает идентификатор элемента.
```js
setToolTip(tooltipText: string): void;
```
где:\
`tooltipText` - текст, который будет отображаться при наведении.
