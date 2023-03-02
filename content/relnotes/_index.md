---
title: "Что нового?"
date: 2022-08-04T12:44:03+03:00
draft: false
weight: 1
---

#### Версия @VERSION@ от @DATE@
- Добавлено <a href="../reference3d/Events">событие</a>:
  - `CAMERA_CHANGE_EVENT` - Событие изменения положения камеры

#### Версия 22.0.7 от 13.12.2022

- Добавлена возможность выбирать элементы на сцене с клавишей CTRL (мультивыбор).
- Добавлена возможность управления видимостью видового куба.
- API получения свойств элементов модели (<a href="../reference3d/Model#getElementProperties">getElementProperties</a>)
- Добавлен метод для центрирования камеры на элементе модели (<a href="../reference3d/Navigation#fitToView">fitToView</a>)
- Добавлен переход к объекту по двойному клику.
- Добавлен переключатель режима отображения модели в настройках.


#### Версия 1.0.6 от 18.11.2022

- API получения скрытых элементов консолидированной модели (<a href="../reference3d/Model#getHiddenElements">подробнее</a>)
- Расширение для просмотра дерева элементов (<a href="../extensions3d/ModelsBrowser">ModelsBrowserExtension</a>)
- Расширение - полноэкранный режим (<a href="../extensions3d/FullScreen">FullScreenExtension</a>)
- Расширение - диалог настроек для 3D просмотрщика (<a href="../extensions3d/ViewerSettings">ViewerSettingsExtension</a>)
- WASD навигация
- Улучшена навиганция
- Добавлены следующие (<a href="../reference3d/Events">события</a>):
  - `SELECTION_CHANGED_EVENT` - измение выделения элемента на сцене
  - `MODEL_PART_LOADED` - событие загрузки части модели в 3D просмотрщик
  - `MODEL_PART_UNLOADED` - событие выгрузки части модели
  - `SETTING_CHANGED_EVENT` - событие изменения настройки 3D просмотрщика
- Скрытие объектов во время навигации


#### Версия 1.0.5 от 04.10.2022

- API управления камерой во вьювере
- API получения скриншота
- Построение дерева. Методы API работы с деревом.
- Событие `VIEWER_RESIZE_EVENT` - событие изменения размеров просмотрщика

