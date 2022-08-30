---
title: "2. Инициализация компонентов"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## Инициализация компонентов

Инициализация компонента PIlot.Web.3D для работы с BIM-моделью:

```js

var viewer;
var options = {};

PilotWeb3D.Initializer(options, () => {
    var htmlDiv = document.getElementById('pilotViewer');
    viewer = PilotWeb3D.CreateViewer(htmlDiv);
    viewer.start();
    console.log('Initialization complete, loading a model next...');
  });
```
Инициализация компонента PIlot.Web.2D для работы с 2D документами:

```js

var viewer;
var options = {};

PilotWeb2D.Initializer(options, () => {
    var htmlDiv = document.getElementById('pilotViewer');
    viewer = PilotWeb2D.CreateViewer(htmlDiv);
    viewer.start();
    console.log('Initialization complete, loading a document next...');
  });
```

#### Initializer

Функцию инициализации достаточно вызвать один раз.

#### Создание экземпляра просмотрщика

Как только функция обратного вызова инициализации `Initializer` была вызвана, мы можем создать экземпляр вьювера.

Пример создания просмотрщика для 3D моделей:

```js
  var htmlDiv = document.getElementById('pilotViewer');
  viewer = PilotWeb3D.CreateViewer(htmlDiv);
```

Пример создания просмотрщика для 2D документов:

```js
  var htmlDiv = document.getElementById('pilotViewer');
  viewer = PilotWeb2D.CreateViewer(htmlDiv);
```

Далее необходимо вызвать метод `viewer.start()`, который инициализирует компонент.

```js
  viewer.start();
```

#### Уничтождение компонентов

Если компоненты больше не нужны на странице их следует уничтожить

```js
  viewer.finish();
  viewer = null;   
```