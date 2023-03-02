---
title: "Events"
date: 2022-11-02T14:44:03+03:00
draft: false
weight: 10
---

## Системные события

### Имена общих событий

```js
class CoreEventTypes {
  // Имя события изменения размера вьювера
  static VIEWER_RESIZE_EVENT: string;
  // Имя события нажатия левой клавиши мыши
  static VIEWER_MOUSE_DOWN_EVENT: string;
  // Имя события перемещения мыши
  static VIEWER_MOUSE_MOVE_EVENT: string;
  // Имя события отпускания левой клавиши мыши
  static VIEWER_MOUSE_UP_EVENT: string;
  // Имя события изменения настройки
  static SETTING_CHANGED_EVENT: string;
  // Имя события восстановления настройки в значение по умолчанию
  static SETTING_RESET_EVENT: string;
}
```

### Имена событий для 3D
```js
class EventTypes extends CoreEventTypes {
  // Имя события изменения селектированного элемента
  static SELECTION_CHANGED_EVENT: string;
  // Имя события загрузки части консолидированной модели
  static MODEL_PART_LOADED: string;
  // Имя события выгрузки части консолидированной модели
  static MODEL_PART_UNLOADED: string;
  // Имя события изменения положения камеры
  static CAMERA_CHANGE_EVENT: string;
}
```

### Классы событий для 3D
```js
// Класс события изменения селектированного элемента
class SelectionChangedEvent extends Event {
  selectedIds: ModelElementIds[]; // массив идентификаторов селектированных элементов
}

// Класс события загрузки или выгрузки части консолидированной модели
class ModelPartEvent extends Event {
  modelPartId: string; // идентификатор части консолидированной модели
}

// Класс события изменения положения камеры
class CameraEvent extends Event {}
```