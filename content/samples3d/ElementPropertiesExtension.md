---
title: "ElementPropertiesExtension"
draft: false
---

**ElementPropertiesExtension** -- пример расширения, которое позволяет просматривать свойства выделенного BIM-элемента.
Расширение имеет имя `ElementPropertiesExtensionSample`.

Пример подключения в `html`:
```html
<link rel="stylesheet" href="https://pilot.ascon.ru/componentkit/components/@VERSION@/samples/ElementPropertiesExtension/ElementPropertiesExtension.css">
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/samples/ElementPropertiesExtension/ElementPropertiesExtension.js"></script>
```

Пример подключения в `javascript`:
```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("ElementPropertiesExtensionSample");
```