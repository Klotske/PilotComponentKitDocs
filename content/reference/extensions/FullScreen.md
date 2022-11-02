---
title: "FullScreenExtension"
date: 2022-11-01T14:44:03+03:00
draft: false
---

**FullScreenExtension** -- расширение, которое позволяет перейти в полноэкранный режим. Также расширение добавляет кнопку на панель интсрументов для управления полноэкранным режимом.

Используйте метод `activate()` для перехода в полноэкранный режим.  \
Расширение имеет имя `PilotWeb3D.FullScreen`.

Пример подключения расширения:
```js
viewer.extensionsLoader.loadExtension('PilotWeb3D.FullScreen')
```

## Методы

### activate()
Перейти в полноэкранный режим
```js
activate(): void;
```
### deactivate()
Выход из полноэкранного режима
```js
deactivate(): void;
```

### getMode()
Получить режим отображения
```js
getMode(): FullScreenExtension.FullScreenMode;
```

## Перечисление FullScreenExtension.FullScreenMode

```js
FullScreenExtension.FullScreenMode.NORMAL
```
Нормальный режим
```js
FullScreenExtension.FullScreenMode.FULLSCREEN
```
Полноэкранный режим

