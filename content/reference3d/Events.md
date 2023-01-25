---
title: "Events"
date: 2022-11-02T14:44:03+03:00
draft: false
weight: 9
---

## Системные события

### Общие события

```js
  class CoreEventTypes {
    // Событие изменения размера вьювера
    static VIEWER_RESIZE_EVENT: string;
    // Событие нажатия левой клавиши мыши
    static VIEWER_MOUSE_DOWN_EVENT: string;
    // Событие перемещения мыши
    static VIEWER_MOUSE_MOVE_EVENT: string;
    // Событие отпускания левой клавиши мыши
    static VIEWER_MOUSE_UP_EVENT: string;
    // Событие изменения настройки
    static SETTING_CHANGED_EVENT: string;
    // Событие восстановления настройки в значение по умолчанию
    static SETTING_RESET_EVENT: string;
  }
```

### События для 3D
```js
  class EventTypes extends CoreEventTypes {
    // Событие изменения селектированного элемента
    static SELECTION_CHANGED_EVENT: string;
    // Событие загрузки части консолидированной модели
    static MODEL_PART_LOADED: string;
    // Событие выгрузки части консолидированной модели
    static MODEL_PART_UNLOADED: string;
    // Событие изменения положения камеры
    static CAMERA_CHANGE_EVENT: string;
  }
```