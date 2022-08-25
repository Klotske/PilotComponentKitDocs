---
title: "Загрузка"
date: 2022-08-04T12:44:03+03:00
draft: false
---

## ЗАГРУЗКА 2D ДОКУМЕНТА

Пример кода для загрузки **2D** документа, где **buffer** – это массив байт 2D (**.xps**) документа:

```Shell

viewer.loadModel(buffer, {}, () => {
    console.log("The document loaded successfully");
},
(m) => {
    console.log("An error occured while loading document: " + m)
});

```

## ЗАГРУЗКА 3D МОДЕЛИ

Пример кода для загрузки **3D** модели, где **buffer** – это массив байт 3D модели в формате **.bm**.

```Shell

viewer.loadModel(buffer, {}, () => {
    console.log("The model loaded successfully");
},
(m) => {
    console.log("An error occured while loading document: " + m)
});

```