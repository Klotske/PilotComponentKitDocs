---
title: "Что нового?"
date: 2022-08-04T12:44:03+03:00
draft: false
weight: 1
---

#### Версия @VERSION@ от @DATE@
- Добавлена возможность читать свойства элемента: <a href="../reference3d/ModelElementProperty/">ModelElementProperty</a>, <a href="../reference3d/ModelElementPropertySet/">ModelElementPropertySet</a> (PI#3-99).
- Реализовано отображение Gizmo и ClippingPlane на отдельном слое (PI#3-351).
- Добавлено <a href="../reference3d/Events">событие</a>:
  - `CAMERA_CHANGE_EVENT` - Событие изменения положения камеры (PI#3-248).
- Добавлены <a href="../reference3d/navigation/Navigation/#setpivotpoint">методы работы с опорной точкой камеры</a> (PI#3-249).
- Изменён метод <a href="../reference3d/Model/#select">select</a>, для выбора части модели добавлен аргумент <a href="../reference3d/SelectionMode/">SelectionMode</a> (PI#3-321, PI#3-324).
- Реализован элемент управления GizmoControl (PI#3-307).
- В расширение <a href="../extensions3d/ModelsBrowser/">ModelsBrowserExtension</a> добавлено мультиселектирование объектов в дереве (PI#3-251).
- Добавлены расширения:
	- <a href="../extensions3d/BoxSelection">BoxSelectionExtension</a> для выделения объектов рамкой (PI#3-197).
	- <a href="../extensions3d/ClippingPlane">ClippingPlaneExtension</a> для установки секущей плоскости (PI#3-335, PI#3-382, PI#3-334).
	- <a href="../samples3d/SceneObserverExtension">SceneObserverExtension</a> - пример работы со слоями (PI#3-369).
- Исправлены ошибки:
	- Исправлено неравномерное перемещение камеры при навигации средней кнопкой мыши (PI#3-294).
	- Исправлена ошибка при вызове метода finish у Viewer3D (PI#3-297).
	- Откорректирована работа дерева при разворачивании узлов выбором объекта в 3D-окне, а сворачивании в дереве (PI#3-273).
	- Исправлено выделение объектов модели после перестроения (PI#3-254).


#### Версия 22.0.7 от 13.12.2022

- Добавлена возможность выбирать элементы на сцене с клавишей CTRL (мультивыбор).
- Добавлена возможность управления видимостью видового куба.
- Добавлено API получения свойств элементов модели (<a href="../reference3d/Model#getElementProperties">getElementProperties</a>)
- Добавлен метод для центрирования камеры на элементе модели (<a href="../reference3d/navigation/Navigation#fitToView">fitToView</a>)
- Добавлен переход к объекту по двойному клику.
- Добавлен переключатель режима отображения модели в настройках.


#### Версия 22.0.6 от 18.11.2022

- Добавлено API получения скрытых элементов консолидированной модели (<a href="../reference3d/Model#getHiddenElements">подробнее</a>)
- Добавлено расширение для просмотра дерева элементов (<a href="../extensions3d/ModelsBrowser">ModelsBrowserExtension</a>)
- Добавлено расширение - полноэкранный режим (<a href="../extensions3d/FullScreen">FullScreenExtension</a>)
- Добавлено расширение - диалог настроек для 3D просмотрщика (<a href="../extensions3d/ViewerSettings">ViewerSettingsExtension</a>)
- Реализована WASD навигация.
- Улучшена навигация.
- Добавлены следующие (<a href="../reference3d/Events">события</a>):
  - `SELECTION_CHANGED_EVENT` - измение выделения элемента на сцене
  - `MODEL_PART_LOADED` - событие загрузки части модели в 3D просмотрщик
  - `MODEL_PART_UNLOADED` - событие выгрузки части модели
  - `SETTING_CHANGED_EVENT` - событие изменения настройки 3D просмотрщика
- Реализовано скрытие объектов во время навигации.


#### Версия 22.0.5 от 04.10.2022

- Добавлено API управления камерой во вьювере.
- Добавлено API для получения скриншота.
- Построение дерева. Методы API работы с деревом.
- Событие `VIEWER_RESIZE_EVENT` - событие изменения размеров просмотрщика.

