---
title: "ModelsBrowserExtension"
date: 2022-11-01T14:44:03+03:00
draft: false
---

**ModelsBrowserExtension** -- расширение, которое позволяет посмотреть дерево элементов загруженных моделей. Также расширение добавляет кнопку на панель интсрументов.

Используйте метод `activate()` для того, чтобы показать дерево элементов.  \
Расширение имеет имя `PilotWeb3D.ModelsBrowser`.

Пример подключения в `html`:
```html
...
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/@VERSION@/extensions/ModelsBrowser3D/ModelsBrowser.css">
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/ModelsBrowser3D/ModelsBrowser.min.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ModelsBrowser");
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