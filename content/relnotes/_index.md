---
title: "What's new?"
date: 2022-08-04T12:44:03+03:00
draft: false
weight: 1
---

## Что нового?

#### Версия @VERSION@ от @DATE@

- API получения скрытых элементов консолидированной модели (<a href="../reference/Model#getHiddenElements">подробнее</a>) {{< ref "reference/Model.md#getHiddenElements" >}}
- Расширение для просмотра дерева элементов (<a href="../reference/extensions/ModelsBrowser">ModelsBrowserExtension</a>)
- Расширение - полноэкранный режим (<a href="../reference/extensions/FullScreen">FullScreenExtension</a>)
- Расширение - диалог настроек для 3D просмотрщика (<a href="../reference/extensions/ViewerSettings">ViewerSettingsExtension</a>)
- WASD навигация
- Улучшена навиганция
- Добавлены следующие (<a href="../reference/Events">события</a>):
  - `SELECTION_CHANGED_EVENT` - измение выделения элемента на сцене
  - `MODEL_PART_LOADED` - событие загрузки части модели в 3D просмотрщик
  - `MODEL_PART_UNLOADED` - событие выгрузки части модели
  - `SETTING_CHANGED_EVENT` - событие изменения настройки 3D просмотрщика
- Скрытие объектов во время навигации


#### Версия 22.0.5 от 04.10.2022

- API управления камерой во вьювере
- API получения скриншота
- Построение дерева. Методы API работы с деревом.
- Событие `VIEWER_RESIZE_EVENT` - событие изменения размеров просмотрщика

