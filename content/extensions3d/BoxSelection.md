---
title: "BoxSelectionExtension"
date: 2023-01-01T14:44:03+03:00
draft: false
---

**BoxSelectionExtension** -- расширение, которое позволяет селектировать элементы с помощью рамки. 
Расширение имеет имя `PilotWeb3D.BoxSelection`.

Пример подключения в `html`:
```html
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/BoxSelection3D/BoxSelection.min.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.BoxSelection");
```
