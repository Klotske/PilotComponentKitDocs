---
title: "ExtensionActivationController"
draft: false,
weight: 14
---

**ExtensionActivationController** -- класс, управляющий активностью расширения.

## Методы

### getActive()
Метод возвращает имя активного расширения.
```js
getActive(): string;
```

### activate()
Метод асинхронно активирует новое расширение. Активное расширение принимает значение ```name``` и инициирует событие, в котором поле ```extensionName``` равно переданному ```name```.
```js
activate(name: string): void;
```
где:\
`name` -- имя нового расширения.

### deactivate()
Метод асинхронно деактивирует расширение. Активное расширение принимает значение ```null``` и инициирует событие, в котором поле ```extensionName``` равно ```null```.
```js
deactivate(): void;
```