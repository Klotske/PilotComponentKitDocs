---
title: "FullScreenExtension"
date: 2022-11-01T14:44:03+03:00
draft: false
weight: 1
---

**FullScreenExtension** -- расширение, которое позволяет перейти в полноэкранный режим. Также расширение добавляет кнопку на панель инструментов для управления полноэкранным режимом.

Используйте метод `activate()` для перехода в полноэкранный режим.  \
Расширение имеет имя `PilotWeb3D.FullScreen`.

Пример подключения в `html`:
```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/extensions/FullScreen3D/FullScreen.min.js"></script>
```

Пример подключения в `javascript`:
```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.FullScreen");
```

## Методы

### activate()
Метод позволяет перейти в полноэкранный режим.
```js
activate(): void;
```
### deactivate()
Метод позволяет выйти из полноэкранного режима.
```js
deactivate(): void;
```

### getMode()
Метод получает режим отображения.
```js
getMode(): FullScreenExtension.FullScreenMode;
```

#### Перечисление FullScreenExtension.FullScreenMode
Нормальный режим:
```js
FullScreenExtension.FullScreenMode.NORMAL
```
Полноэкранный режим:
```js
FullScreenExtension.FullScreenMode.FULLSCREEN
```


