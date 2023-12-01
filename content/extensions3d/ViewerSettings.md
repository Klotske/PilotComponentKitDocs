---
title: "ViewerSettingsExtension"
date: 2022-11-01T14:44:03+03:00
draft: false
---

**ViewerSettingsExtension** -- расширение, которое позволяет посмотреть настройки просмотрщика 3D моделей. Также расширение добавляет кнопку на панель интсрументов.

Используйте метод `activate()` для того, чтобы показать диалог настроек просмотрщика 3D моделей.  \
Расширение имеет имя `PilotWeb3D.ViewerSettings`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/ViewerSettings3D/ViewerSettings.min.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.ViewerSettings");
```

## Методы

### activate()
Показать диалог настроек просмотрщика 3D моделей
```js
activate(): void;
```
### deactivate()
Скрыть диалог настроек просмотрщика 3D моделей
```js
deactivate(): void;
```