---
title: "IconsSet"
date: 2023-07-31T17:11:03+03:00
draft: false
---

**IconsSet** -- класс-хранилище иконок.

## Список доступных иконок:
```js
 export namespace Viewer3DIcons {
  export const VIEWER_SETTINGS_ICON: string;
  export const VIEWER_MODEL_BROWSER_ICON: string;
  export const VIEWER_FULL_SCREEN_ICON: string;
  export const VIEWER_COLLAPSE_ICON: string;
  export const VIEWER_ELEMENT_PROPERTIES_ICON: string;
  export const VIEWER_ADD_CLIPPING_PLANE_ICON: string;
  export const VIEWER_CLIPPING_FLIP_ICON: string;
  export const VIEWER_DELETE_CLIPPING_PLANE_ICON: string;
  export const VIEWER_CLIPPING_CUBE_ICON: string;
  export const VIEWER_DISABLED_DELETE_CLIPPING_PLANE_ICON: string;
  export const VIEWER_DISABLED_CLIPPING_FLIP_ICON: string;
  export const VIEWER_ADD_REMARK_ICON: string;
}

export namespace ViewerGeneralIcons {
  export const ZOOM_IN: string;
  export const ZOOM_OUT: string;
  export const CLOSE: string;
  export const STRETCH_WINDOW: string;
  export const EXPAND_TREE: string;
  export const COLLAPSE_TREE: string;
  export const ARROW_DROP_DOWN: string;
  export const ARROW_DROP_RIGHT: string;
  export const CIRCLE_ICON: string;
}
```

## Пример использования:
Использовать как html элемент, а именно через свойство innerHTML.
```js
  element.innerHTML = PilotWeb3D.Viewer3DIcons.VIEWER_SETTINGS_ICON
```

## Кастомное объявление иконки:
Чтобы добавить иконку:
1. Сохранить svg представление иконки в виде строки.
2. Вставить иконку с помощью innerHTML.
```js
export class IconExample {
  private readonly EXAMPLE_ICON  = `
        <?xml version="1.0" encoding="UTF-8"?>
        <svg version="1.0" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">...</svg>`

  hereAddIcon(): void {
    ...
    const element = document.getElementById('myDiv');
    element.innerHTML = this.EXAMPLE_ICON;
    ...
  }
}
```
