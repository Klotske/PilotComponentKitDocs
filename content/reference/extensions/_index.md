---
title: "Extensions"
date: 2022-08-04T12:44:03+03:00
draft: false
weight: 11
---

Компоненты работы с BIM-моделями и документами поддерживают расширение функциональности с помощью подключаемых модулей расширений. Система **PilotCloud** включает в себя набор модулей расширений, которые при необходимости могут быть подключены. Каждый модуль расширения в этом списке вносит новые возможности в компоненты системы. Если вам нужно добавить специализированные функции Вы можете создавать свои собственные расширения.

## Модули расширения

### FullScreenExtension
Модуль расширения для управления полноэкранным режимом

Пример подлючения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/1.0.6/extensions/FullScreen/FullScreen.min.js"></script>
```

Пример подлючения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.FullScreen");
```

### ModelsBrowserExtension
Модуль расширения для просмотра дерева элементов

Пример подлючения в `html`:
```html
...
<link rel="stylesheet" href="https://pilotcloud.ascon.net/components/1.0.6/extensions/ModelsBrowser/ModelsBrowser.css">
...
<script src="https://pilotcloud.ascon.net/components/1.0.6/extensions/ModelsBrowser/ModelsBrowser.min.js"></script>
...
```

Пример подлючения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ModelsBrowser");
```

### ViewerSettingsExtension
Модуль расширения для управления настройками компонента.

Пример подлючения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/1.0.6/extensions/ViewerSettings/ViewerSettings.min.js"></script>
```

Пример подлючения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ViewerSettings");
```
