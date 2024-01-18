---
title: "ExtensionActivationController"
draft: false,
weight: 14
---

**ExtensionActivationController** -- класс, управляющий изменением выбранного расширения.

## Методы

### getActive()
Метод возвращает имя активного расширения.
```js
getActive(): string;
```

### activate()
Метод активирует новое расширение. Активное расширение принимает значение ```name``` и выбрасывает событие, в котором поле ```extensionName``` равно переданному ```name```.
```js
activate(name: string): void;
```
где:\
`name` -- имя нового расширения.

### deactivate()
Метод деактивирует расширение. Активное расширение принимает значение ```null``` и выбрасывает событие, в котором поле ```extensionName``` равно ```null```.
```js
deactivate(): void;
```