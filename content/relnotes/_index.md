---
title: "Что нового?"
draft: false
weight: 1
---

#### Версия @VERSION@ от @DATE@

- Добавлена возможность изменения размеров диалоговых окон.
- Добавлена возможность перетаскивания диалоговых окон.
- Поднята версия компонента `Three.js` до версии `0.151.3`.
- Реализована настройка положения панели инструментов для компонентов **PilotWeb3D** и **PilotWeb2D** -- <a href="../reference3d/configuration/ViewerConfiguration">ViewerConfiguration</a>.
- Добавлена возможно указать префикс к имени для клиентских настроек при сохранение в `LocalStorage`.
- Добавлена поддержка языков -- <a href="../reference/Localization">Localization</a>.
- Исправлены ошибки:
  - Исправлена ошибка управления настройками сцены (PI#3-756).
  - Исправлена ошибка возникающая при отмене загрузки модели (PI#3-370).
  - Исправлено отображение линий на 3D сцене (PI#3-669).
  - Исправлена ошибка связанная с поддержкой 3D сцены на мобильных устройствах (PI#3-769)


#### Версия 23.0.4 от 17.06.2023

- Новая стилизация панели инструментов в компонентах. 
- Реализовано чтение строительных осей в компоненте **PilotBimDataprovider** (PI#3-597).
- Реализовано отображение строительных осей в компоненте **PilotWeb3D** (PI#3-681).
- Поправлено отображение имени элемента при отсутствии имени в модели. Модуль расширения **ModelBrowserExtension** (PI#3-671).
- Реализовано изменение направления секущей плоскости в модуле расширения **ClippingPlaneExtension** (PI#3-719).
- Новая стилизация диалоговых окон в модулях расширений.
- Исправлены ошибки:
  - Исправлено отображение свойств элемента в модуле расширения **ElementPropertiesExtension** (PI#3-474).
  - Исправлено положение надписи "Загрузка" в компонентах (PI#3-602).
  - Исправлена ошибка очистки сцены при закрытии (PI#3-717).


#### Версия 23.0.3 от 15.05.2023

- Выпущен новый npm-пакет <a href="https://www.npmjs.com/package/@pilotdev/pilot-bim-dataprovider" target="blank">@pilotdev/pilot-bim-dataprovider</a> для чтения данных из информационной модели (BIM).
- Добавлен npm-пакет с определениями типов (TypeScript) для компонента **PilotWeb3D** -- <a href="https://www.npmjs.com/package/@pilotdev/pilot-web-3d" target="blank">@pilotdev/pilot-web-3d</a>.
- **ClippingPlaneExtension**: Поправлен цвет плоскости сечения. (PI#3-524)
- **ClippingPlaneExtension**: добавлен новый вид сечений -- куб сечений. (PI#3-523)
- Новая стилизация элемента управления <a href="../reference3d/gizmo">GizmoControl</a>. (PI#3-385)
- Добавлены методы <a href="../reference2d/Viewer2D#unloadDocument">выгрузки</a> документа из **PilotWeb2D**. (PI#3-537)
- Обеспечена совместимость с моделями <a href="https://pilot.ascon.ru" target="blank">Pilot-BIM-Server</a> версии 23.15 и старше.
- Исправлены ошибки:
  - Добавлена блокировка событий мыши, клавиатуры и сенорной панели при потере фокуса вьювером **PilotWeb3D**. (PI#3-530) 
  - Поправлено отображение картинок в компоненте **PilotWeb2D**. (PI#3-562) 


#### Версия 23.0.2 от 07.04.2023

- **ClippingPlaneExtension**: Реализована возможность удалить плоскость сечения.
- Реализовано API для элемента управления <a href="../reference3d/gizmo">GizmoControl</a>.
- Исправлены ошибки:
  - Убрано отображение плоскостей сечения после выгрузки модели.
  - Загрузка расширений сразу после старта **PilotWeb3D**.
  - Исправлена совместная работа расширений **BoxSelectionExtension** и **ClippingPlaneExtension**.
- Добавлено расширение:
  - <a href="../extensions3d/WasdNavigation/">WasdNavigationExtension</a> для навигации клавишами WASD.


#### Версия 23.0.1 от 03.03.2023

- Добавлена возможность читать свойства элемента: <a href="../reference3d/ModelElementProperty/">ModelElementProperty</a>, <a href="../reference3d/ModelElementPropertySet/">ModelElementPropertySet</a> (PI#3-99).
- Реализовано отображение Gizmo и ClippingPlane на отдельном слое (PI#3-351).
- Добавлено <a href="../reference3d/Events">событие</a>:
  - `CAMERA_CHANGE_EVENT` - Событие изменения положения камеры (PI#3-248).
- Добавлены <a href="../reference3d/navigation/INavigation/#setpivotpoint">методы работы с опорной точкой камеры</a> (PI#3-249).
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
	- Откорректирована работа дерева при разворачивании узлов выбором объекта в 3D-окне (PI#3-273).
	- Исправлено выделение объектов модели после перестроения (PI#3-254).


#### Версия 22.0.7 от 13.12.2022

- Добавлена возможность выбирать элементы на сцене с клавишей CTRL (мультивыбор).
- Добавлена возможность управления видимостью видового куба.
- Добавлено API получения свойств элементов модели (<a href="../reference3d/Model#getElementProperties">getElementProperties</a>)
- Добавлен метод для центрирования камеры на элементе модели (<a href="../reference3d/navigation/INavigation#fitToView">fitToView</a>)
- Добавлен переход к объекту по двойному клику.
- Добавлен переключатель режима отображения модели в настройках.


#### Версия 22.0.6 от 18.11.2022

- Добавлено API получения скрытых элементов консолидированной модели (<a href="../reference3d/Model#getHiddenElements">Подробнее:</a>)
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

