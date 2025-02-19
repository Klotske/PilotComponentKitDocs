---
title: Встроенные расширения
date: 2025-01-10
draft: false
weight: 0
---

Встроенные модули расширения в `Viewer3D` загружаются автоматически при запуске вьювера. Для каждого встроенного модуля можно указать начальные настройки, которые описаны в документации модуля.

Чтобы задать настройку для встроенного расширения, необходимо указать её в специальном свойстве конфигурации вьювера.

Например, настройка для загрузки встроенного расширения `PilotWeb3D.ViewCube`:

```js
const configuration = new PilotWeb3D.Viewer3DConfiguration();
configuration.extensionsOptions = {
  'PilotWeb3D.ViewCube': {
    disabled: true
  },
};
```

В данном примере указано, что вьювер не должен загружать это расширение. Все встроенные расширения поддерживают настройку `disabled` и могут быть исключены из загрузки вьювера.

Компонент `Viewer3D` содержит следующие встроенные модули расширения:
- [PilotWeb3D.ViewCube](./ViewCube)
- [PilotWeb3D.NavigationMark](./NavigationMark)
- [PilotWeb3D.RenderOptions](./RenderOptions).
