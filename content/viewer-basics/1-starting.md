---
title: "Добавить компоненты на HTML страницу"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 1
---

Следующий пример показывает как добавить компонент для работы с **BIM-моделью** на вашу HTML страницу.

```html
<head>
    <meta name="viewport" content="width=device-width, minimum-scale=1.0, initial-scale=1, user-scalable=no" />
    <meta charset="utf-8">

    <link rel="stylesheet" href="https://pilotcloud.ascon.net/components/@VERSION@/pilotweb3d/style.css" type="text/css">
    <script src="https://pilotcloud.ascon.net/components/@VERSION@/pilotweb3d/pilotweb3d.min.js"></script>

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

Следующий пример показывает, как добавить компонент для работы с **документами** на вашу HTML страницу.

```html
<head>
    <meta name="viewport" content="width=device-width, minimum-scale=1.0, initial-scale=1, user-scalable=no" />
    <meta charset="utf-8">

    <link rel="stylesheet" href="https://pilotcloud.ascon.net/components/@VERSION@/pilotweb2d/style.css" type="text/css">
    <script src="https://pilotcloud.ascon.net/components/@VERSION@/pilotweb2d/pilotweb2d.min.js"></script>

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

{{< hint type="tip" title="Совет" >}}
Пакеты **PilotWeb3D** и **PilotWeb2D** имеют довольно большой размер, поэтому мы рекомендуем подключать эти библиотеки к странице HTML как можно позже.	
{{< /hint >}}


