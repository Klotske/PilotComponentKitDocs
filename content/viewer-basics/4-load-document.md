---
title: "Загрузка документа"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 40
---

Компонент **PilotWeb2D** предназначен для просмотра документов в формате **XPS**. Никаких предварительных требований для работы с документом нет.

Пример загрузки документа:
```js
  let options = {};
  let buffer = // ArrayBuffer from xps document
  viewer.loadDocument(buffer, {})
    .then(() => console.log(`The document loaded successfully`))
    .catch((e) => console.error(`An error occured while loading document: ${e}`));
```

{{< hint type="note" title="Примечание">}}
`buffer` - это массив байт полученный из файла **.xps**.
{{< /hint >}}