---
title: "MeasurementToolsExtension"
date: 2023-09-01T14:44:03+03:00
draft: false
---

**MeasurementToolsExtension** -- расширение, которое предоставляет различные инструменты измерений.

Расширение имеет имя `PilotWeb3D.MeasurementTools`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/23.0.10/extensions/MeasurementTools3D/MeasurementTools.min.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.MeasurementTools");
```

## Методы

### activate()
Активировать расширение
```js
activate(): void;
```
### deactivate()
Деактивировать расширение
```js
deactivate(): void;
```