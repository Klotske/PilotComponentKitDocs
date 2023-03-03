---
title: "ElementPropertiesExtension"
draft: false
---

**ElementPropertiesExtension** -- пример расширения, которое позволяет просматривать свойства селектированного бим-элемента.
Расширение имеет имя `ElementPropertiesExtensionSample`.

Пример подключения в `html`:
```html
...
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/@VERSION@/extensions/samples/ElementPropertiesExtension/ElementPropertiesExtension.css">
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/samples/ElementPropertiesExtension/ElementPropertiesExtension.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("ElementPropertiesExtensionSample");
```