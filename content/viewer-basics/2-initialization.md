---
title: "Инициализация компонентов"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 20
---

Инициализация компонента **PilotWeb3D** для работы с BIM-моделью:

```js
var viewer;
var options = {};

PilotWeb3D.Initializer(options, async () => {
    var htmlDiv = document.getElementById('pilotViewer');
    viewer = PilotWeb3D.CreateViewer(htmlDiv);
    await viewer.start();
    console.log('Initialization complete, loading a model next...');
  });
```
Инициализация компонента **PIlotWeb2D** для работы с документами:

```js
var viewer;
var options = {};

PilotWeb2D.Initializer(options, async () => {
    var htmlDiv = document.getElementById('pilotViewer');
    viewer = PilotWeb2D.CreateViewer(htmlDiv);
    await viewer.start();
    console.log('Initialization complete, loading a document next...');
  });
```

{{< hint type="note" title="Примечание">}}
Функцию инициализации достаточно вызвать один раз.
{{< /hint >}}

### Пример создания экземпляров компонентов

Как только функция обратного вызова инициализации `Initializer` была вызвана, мы можем создать экземпляр `GuiViewer3D`.

Пример создания компонента для BIM-моделей:

```js
  let htmlDiv = document.getElementById('pilotViewer');
  let viewer = PilotWeb3D.CreateViewer(htmlDiv);
```

Пример создания компонента для документов:

```js
  let htmlDiv = document.getElementById('pilotViewer');
  let viewer = PilotWeb2D.CreateViewer(htmlDiv);
```

Далее необходимо вызвать метод `start()`, который инициализирует компонент:

```js
  await viewer.start();
```

### Освобождение ресурсов

Если компоненты больше не нужны на странице, следует завершить их работу:

```js
  await viewer.finish();
  viewer = null;
```