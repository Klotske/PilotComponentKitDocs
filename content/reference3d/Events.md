---
title: "Events"
date: 2022-11-02T14:44:03+03:00
draft: false

---

## Системные события

### Имена общих событий

```js
class CoreEventTypes {
  // Имя события изменения размера просмотрщика
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
  // Имя события загрузки расширения. Вызывается после загрузки расширения
  static EXTENSION_LOADED;
  // Имя события выгрузки расширения. Вызывается непосредственно перед выгрузкой расширения
  static EXTENSION_UNLOADING;
  // Имя события выгрузки расширения. Вызывается после выгрузки расширения
  static EXTENSION_UNLOADED;
}
```

### Имена событий для 3D {#Events3D}
```js
class EventTypes extends CoreEventTypes {
  // Имя события изменения селектированного элемента
  static SELECTION_CHANGED_EVENT: string;
  // Имя события загрузки части консолидированной модели
  static MODEL_PART_LOADED: string;
  // Имя события выгрузки части консолидированной модели
  static MODEL_PART_UNLOADED: string;
  // Имя события обновления части консолидированной модели
  static MODEL_PART_UPDATED: string;
  // Имя события изменения положения виртуального начала координат
  static VIRTUAL_ORIGIN_CHANGED: string;
  // Имя события изменения положения камеры
  static CAMERA_CHANGE_EVENT: string;
  // Имя события изменения типа навигации камеры
  static CAMERA_NAVIGATION_MODE_CHANGED_EVENT: string;
  // Имя события клика по отрисованному элементу
  static RENDER_CLICK_EVENT: string;
  // Имя события ховера отрисованного элемента
  static RENDER_HOVER_EVENT: string;
  // Имя события двойного клика по отрисованному элементу
  static RENDER_DOUBLE_CLICK_EVENT: string;
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

// Класс события обновления части консолидированной модели
class ModelPartUpdateEvent extends ModelPartEvent {
  updatedElementIds?: string[]; // идентификаторы обновлённых элементов модели
  removedElementIds?: string[]; // идентификаторы удалённых элементов модели
  addedElementIds?: string[]; // идентификаторы добавленных элементов модели
}

// Класс события изменения виртуального начала координат
class VirtualOriginEvent extends Event {
  virtualOrigin: Point3; // обновлённое положение виртуального начала координат
  delta: Point3; // смещение объектов на сцене: oldOrigin - newOrigin
}

// Класс события изменения положения камеры
class CameraEvent extends Event {}

// Класс события клика по отрисованному элементу
class ClickedEvent extends Event {
  modelId: string; // идентификатор модели
  modelElementId: string; // идентификатор элемента модели
  ctrlKey: boolean; // флаг нажатия клавиши Ctrl
}

// Класс события ховера отрисованного элемента
class HoverEvent extends Event {
  modelId: string; // идентификатор модели
  modelElementId: string; // идентификатор элемента модели
}

// Класс события загрузки или выгрузки расширения
class ExtensionEvent extends Event {
  extensionName: string;
}
```