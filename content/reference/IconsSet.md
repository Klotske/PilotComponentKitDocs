---
title: "IconsSet"
date: 2023-07-31T17:11:03+03:00
draft: false
---

**IconsSet** -- класс для регистрации новых svg иконок.

Для регистрации иконки:
1. Добавить файл иконки в путь core/src/assets/svg.
2. Добавить новое или использовать существующее пространство имён
3. Экспортировать иконку как переменную, используя svg-inline-loader и функцию require
4. Прописать путь до иконки с префиксом !!svg-inline-loader!

## Пример:
```js
  export const VIEWER_SETTINGS_ICON: string = require('!!svg-inline-loader!../assets/svg/settings.svg');
```

## Пример c пространством имён:
```js
  export namespace Viewer3DIcons {
    export const VIEWER_SETTINGS_ICON: string = require('!!svg-inline-loader!../assets/svg/settings.svg');
    ...
  }
```

## Пример использования:
Использовать как html элемент, а именно через свойство innerHTML
```js
  element.innerHTML = PilotWeb3D.Viewer3DIcons.VIEWER_SETTINGS_ICON
```
