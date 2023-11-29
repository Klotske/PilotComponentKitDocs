---
title: "ZoomExtension"
draft: false
weight: 1
---

**ZoomExtension** -- расширение, которое добавляет элементы управления масштабом документа в панель инструменотов компонента **PIlotWeb2D**.

Расширение имеет имя `PilotWeb2D.Zoom`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/23.0.10/extensions/Zoom2D/Zoom.min.js"></script>
```

Пример подключения в `javascript`:
```js
const htmlDiv = document.getElementById('pilotViewer')
const configuration = new PilotWeb2D.Viewer2DConfiguration();
const viewer = PilotWeb2D.CreateViewer(htmlDiv, configuration);
await viewer.start();
// загружаем расширение. Расширение активируется автоматически
const extension = await viewer.extensionsLoader.loadExtension("PilotWeb2D.Zoom");
```