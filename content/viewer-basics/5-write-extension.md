---
title: "Создание расширения"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 50
---

С помощью расширений можно дополнять функциональность компонентов работы с BIM-моделями и документами.

#### Шаг 1. Подключение файла расширения
Расширение должно быть подключено после подключения всех классов ядра компонента **PilotWeb3D** или **PilotWeb2D**. 
Пример для подключения расширения `my-extension.js`:

```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/pilotweb3d/pilotweb3d.min.js"></script>
<script src="my-extension.js"></script>
```

#### Шаг 2. Пишем код расширения
Чтобы написать свое расширение для компонентов необходимо:

1. Унаследоваться от класса `PilotWeb3D.Extension` или `PilotWeb2D.Extension`.
2. Зарегистрировать расширение с уникальным именем в системе.

Пример:

```js
class My3DExtension extends PilotWeb3D.Extension {
    
  constructor(viewer) {
    super(viewer);
  }

  getName() {
    return 'My3DExtension';
  }

  load() {
    super.load();
    alert('My3DExtension is loaded!')
    return true;
  }

  unload() {
    super.unload();
    alert('My3DExtension is unloaded!')
    return true;
  }
}

PilotWeb3D.theExtensionManager.registerExtensionType('My3DExtension', My3DExtension);
```

#### Шаг 3. Загрузка расширения

Пример загрузки расширения для компонента **PilotWeb3D**:

```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("My3DExtension");
...
await viewer.loadModelPart(...);
```

Пример загрузки расширения для компонента **PilotWeb2D**:

```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb2D.CreateViewer(htmlDiv);
await viewer.start();
viewer.extensionsLoader.loadExtension("My2DExtension");
...
await viewer.loadDocument(...);
```
