---
title: "Загрузка частей модели"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## Загрузка частей модели в 3D компонент

Перед загрузкой части модели ее необходимо получить из системы Pilot-BIM. После получения части модели ее можно загрузить в компонент Pilot.Web.3D

Пример загрузки одной модели:
```js
  let options = { 
    Guid: bmFileId
  };
  let buffer = // ArrayBuffer from .bm file

  viewer.loadModelPart(buffer, options, () => {
    console.log(`${options.Guid}: The model loaded successfully`);
  },(e) => {
    console.error(`${options.Guid}: An error occured while loading model part: ${e}`);
  });
```

Пример загрузки части модели:
```js
  let options = { 
    isConsolidatedModel: true,
    Guid: bmFileId
  };
  let buffer = // ArrayBuffer from .bm file
  
  viewer.loadModelPart(duffer, options, () => {
    console.log(`${options.Guid}: The model loaded successfully`);
  },(e) => {
    console.error(`${options.Guid}: An error occured while loading model part: ${e}`);
  });
```

{{< hint type=[note]>}}
Чтобы добавить часть модели к уже загруженным частям в `options` следует задать параметр `isConsolidatedModel : true`
{{< /hint >}}

{{< hint type=[note]>}}
`Guid` - следует указывать уникальный идентифкатор части модели в рамках одной консолидированной модели.
{{< /hint >}}

{{< hint type=[note]>}}
`buffer` - это массив байт полученный из файла **.bm** из системы **Pilot-BIM**.
{{< /hint >}}