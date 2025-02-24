---
title: "RenderOptionsExtension"
date: 2025-02-19
draft: false
---

**RenderOptionsExtension** — расширение, управляющее настройками отображения дополнительных объектов на сцене, таких как "заполнители проёмов" и "заполнители помещений". По умолчанию эти объекты отключены. Это расширение добавляет кнопку с выпадающим списком в панель инструментов, позволяя управлять этими опциями.

Расширение имеет имя `PilotWeb3D.RenderOptions`.

Чтобы отключить загрузку этого расширения, установите в настройках просмотрщика параметр `disabled` в `true` для этого модуля расширения.


```js
const configuration = new PilotWeb3D.Viewer3DConfiguration();
configuration.extensionsOptions = {
  'PilotWeb3D.RenderOptions': {
    disabled: true
  },
};
```

Этому модулю расширения можно задать индекс для расположения его в панели инструментов с помощью следующей настройки:

```js
const configuration = new PilotWeb3D.Viewer3DConfiguration();
configuration.extensionsOptions = {
  'PilotWeb3D.RenderOptions': {
    toolbarIndex: 5,
  },
};
```