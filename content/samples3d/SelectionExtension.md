---
title: "SelectionExtension"
draft: false
---

**SelectionExtension** -- пример расширения, которое показывает возможности работы различного `API` компонента **PilotWeb3D**.
Расширение имеет имя `Selection3DExtension`.

Пример подключения в `html`:
```html
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/23.0.10/samples/SelectionExtension/SelectionExtension.css">
<script src="https://pilotcloud.ascon.net/components/23.0.10/samples/SelectionExtension/SelectionExtension.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("Selection3DExtension");
```