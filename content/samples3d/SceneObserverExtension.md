---
title: "SceneObserverExtension"
draft: false
---

**SceneObserverExtension** -- пример расширения, которое позволяет просматривать и управлять 3D сценами.
Расширение имеет имя `PilotWeb3D.SceneObserver`.

Пример подключения в `html`:
```html
...
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/@VERSION@/extensions/samples/SceneObserver/SceneObserverExtension.css">
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/samples/SceneObserver/SceneObserverExtension.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.SceneObserver");
```
