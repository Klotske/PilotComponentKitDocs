---
title: "MeasurementToolsExtension"
date: 2023-09-01T14:44:03+03:00
draft: false
---

**MeasurementToolsExtension** -- расширение, которое предоставляет различные инструменты измерений.

Расширение имеет имя `PilotWeb3D.MeasurementTools`.

Пример подключения в `html`:
```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/extensions/MeasurementTools3D/MeasurementTools.min.js"></script>
```

Пример подключения в `javascript`:
```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.MeasurementTools");
```

## Методы

### activate()
Активирует расширение.
```js
activate(): void;
```
### deactivate()
Деактивирует расширение.
```js
deactivate(): void;
```

### getToolIDs()
Возвращает список идентификаторов всех инструментов измерений на сцене.
```js
getToolIDs(): string[];
```

### removeTools()
Удаляет инструменты измерений со сцены.
```js
removeTools(toolIDs?: string[]): void;
```
где:\
`toolIDs` -- список идентификаторов инструментов измерений для удаления. Необязательный параметр. Если не задан, то удаляются все инструменты измерений.
