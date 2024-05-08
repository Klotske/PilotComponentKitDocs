---
title: "ZoomToFitExtension"
date: 2022-11-01T14:44:03+03:00
draft: false
---

**ZoomToFitExtension** -- расширение, которое добавляет на панель инструментов кнопку масштабирования по всем объектам сцены.

Расширение имеет имя `PilotWeb3D.ZoomToFit`.

Пример подключения в `html`:
```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/extensions/ZoomToFit3D/ZoomToFit.min.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ZoomToFit");
```