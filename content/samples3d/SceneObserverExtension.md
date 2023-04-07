---
title: "SceneObserverExtension"
draft: false
---

**SceneObserverExtension** -- пример расширения, которое позволяет просматривать дерево графических объектов на сцене. Также расширение добавляет кнопку на панель интсрументов.
Расширение имеет имя `PilotWeb3D.SceneObserver`.

Пример подключения в `html`:
```html
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/@VERSION@/samples/SceneObserverExtension/SceneObserverExtension.css">
<script src="https://pilotcloud.ascon.net/components/@VERSION@/samples/SceneObserverExtension/SceneObserverExtension.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.SceneObserver");
```
## Методы

### activate()
Показать дерево графических объектов.
```js
activate(): void;
```
### deactivate()
Скрыть дерево графических объектов.
```js
deactivate(): void;
```
