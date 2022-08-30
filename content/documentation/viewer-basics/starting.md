---
title: "1. Добавить компоненты на HTML страницу"
date: 2022-08-29T14:44:03+03:00
draft: false
---

## Добавить компонент на HTML страницу

Следующий код показывает как добавить компонент работы с BIM-моделью на вашу HTML страницу.

```html
<head>
    <meta name="viewport" content="width=device-width, minimum-scale=1.0, initial-scale=1, user-scalable=no" />
    <meta charset="utf-8">

    <link rel="stylesheet" href="https://pilotcloud.ascon.net/components/1.0.0/pilotweb3d/style.css" type="text/css">
    <script src="https://pilotcloud.ascon.net/components/1.0.0/pilotweb3d/pilotweb3d.min.js"></script>

    <style>
        body {
            margin: 0;
        }
        #pilotViewer {
            width: 100%;
            height: 100%;
            margin: 0;
        }
    </style>
</head>
<body>
  <div id="pilotViewer"></div>
</body>
```

Следующий код показывает как добавить компонет работы с  документами на вашу HTML страницу.

```html
<head>
    <meta name="viewport" content="width=device-width, minimum-scale=1.0, initial-scale=1, user-scalable=no" />
    <meta charset="utf-8">

    <link rel="stylesheet" href="https://pilotcloud.ascon.net/components/1.0.0/pilotweb2d/style.css" type="text/css">
    <script src="https://pilotcloud.ascon.net/components/1.0.0/pilotweb2d/pilotweb2d.min.js"></script>

    <style>
        body {
            margin: 0;
        }
        #pilotViewer {
            width: 100%;
            height: 100%;
            margin: 0;
        }
    </style>
</head>
<body>
  <div id="pilotViewer"></div>
</body>
```

#### Размер пакета

Размер пакетов Pilot.Web.3D и Pilot.Web.2D не маленькие, по-это мы рекомендуем подключать эти библиотеки к HTML странице как можно позже.