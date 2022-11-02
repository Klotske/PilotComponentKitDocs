---
title: "ModelsBrowserExtension"
date: 2022-11-01T14:44:03+03:00
draft: false
---

**ModelsBrowserExtension** -- расширение, которое позволяет посмотреть дерево элементов загруженных моделей. Также расширение добавляет кнопку на панель интсрументов.

Используйте метод `activate()` для того, чтобы показать дерево элементов.  \
Расширение имеет имя `PilotWeb3D.ModelsBrowser`.

Пример подключения расширения:
```js
viewer.extensionsLoader.loadExtension('PilotWeb3D.ModelsBrowser')
```

## Методы

### activate()
Показать дерево элементов
```js
activate(): void;
```
### deactivate()
Скрыть дерево элементов
```js
deactivate(): void;
```