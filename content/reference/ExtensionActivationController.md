---
title: "ExtensionActivationController"
draft: false,
weight: 14
---

**ExtensionActivationController** -- класс, управляющий изменением выбранного расширения.

## Методы

### getActive()
Метод возвращает имя выбранного расширения.
```js
getActive(): string;
```

### activate()
Метод устанавливает новое расширение.
```js
activate(name: string): void;
```
где:\
`name` -- имя нового расширения.

### deactivate()
Метод деактивирует расширение. Активное расширение принимает значение null и выбрасывает событие в котором поле extensionName равен ```null```
```js
deactivate(): void;
```