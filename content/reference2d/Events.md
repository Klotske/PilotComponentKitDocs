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
    // Имя события загрузки расширения. Вызывается после загрузки расширения
    static EXTENSION_LOADED;
    // Имя события выгрузки расширения. Вызывается непосредственно перед выгрузкой расширения
    static EXTENSION_UNLOADING;
    // Имя события выгрузки расширения. Вызывается после выгрузки расширения
    static EXTENSION_UNLOADED;
  }
```

### Классы событий для 2D
```js
// Класс события загрузки или выгрузки расширения
class ExtensionEvent extends Event {
  extensionName: string;
}
```