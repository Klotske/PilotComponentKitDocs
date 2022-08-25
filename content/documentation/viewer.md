---
title: "Просмотрщик Pilot-Web-Viewer"
date: 2022-08-04T12:44:03+03:00
draft: false
---

## ДОБАВЛЕНИЕ PILOT-WEB-VIEWER НА СТРАНИЦУ HTML

Следующий фрагмент разметки HTML показывает как встроить Pilot-Web-Viewer на страницу HTML:

{{< highlight html >}}
<head>
    <meta name="viewport" content="width=device-width, minimum-scale=1.0, initial-scale=1, user-scalable=no" />
    <meta charset="utf-8">
 
    <link rel="stylesheet" href="https://developer.api.ascon.net/pilot.web.viewer/v1/viewers/7.*/style.min.css" type="text/css">
    <script src="https://developer.api.ascon.net/pilot.web.viewer/v1/viewers /7.*/viewer3D.min.js"></script>
 
    <style>
        body {
            margin: 0;
        }
        #pilotViewer {
            width: 100%;
            height: 100%;
            margin: 0;
            background-color: #F0F8FF;
        }
    </style>
</head>
<body>
    <div id="pilotViewer"></div>
</body>
{{< /highlight >}}

Элемент *div* с идентификатором *pilotViewer* инициализируется экземпляром *Pilot-Web-Viewer*. См. **Инициализация Viewer**.

{{< hint type="note" icon=gdoc_github  title="Примечание">}}
    Pilot-Web-Viewer зависит от библиотеки JavaScript — Three.js
{{< /hint >}}

---

## РАЗМЕР БАНДЛА

Библиотека JavaScript — Three.js — довольно объёмная. Поэтому мы рекомендуем использовать тэг *&lt;script&gt;* как можно ближе к концу страницы, 
чтобы позволить браузеру вначале прочитать её.

---

## ВЕРСИИ PILOT-WEB-VIEWER

Тэг *&lt;script&gt;* указывает местоположение встроенного в просмотрщик JavaScript-кода, а также версию библиотеки для загрузки. 
В приведённом ниже примере HTML-разметки обозначена версия 7.*. Она извлекает последнюю младшую версию, доступную для основной версии 7.

Например, если доступны версии 7.0, 7.1, 7.2, то при запрашиваемой просмотрщиком версии 7.* будет извлечена 7.2.

Указанная версия также может включать номера младших версий и исправлений. В приведённых ниже примерах все варианты являются допустимыми.

{{< highlight html >}}

<!-- Fetch exactly version 7.0.0 -->
<script src="https://developer.api.autodesk.com/modelderivative/v2/viewers/7.0.0/viewer3D.min.js"></script>
 
<!-- Fetch latest patch version for 7.0 -->
<script src="https://developer.api.autodesk.com/modelderivative/v2/viewers/7.0.*/viewer3D.min.js"></script>
 
<!-- Also fetch latest patch version for 7.0 -->
<script src="https://developer.api.autodesk.com/modelderivative/v2/viewers/7.0/viewer3D.min.js"></script>
 
<!-- Fetch latest minor version for 7.0 -->
<script src="https://developer.api.autodesk.com/modelderivative/v2/viewers/7.*/viewer3D.min.js"></script>

{{< /highlight >}}

---

## ИНИЦИАЛИЗАЦИЯ PILOT-WEB-VIEWER

Функция инициализации Pilot-Web-Viewer должна быть запущена только один раз. Она помогает убедиться, что все подсистемы запущены перед началом процесса.

Инициализация проходит в 2 этапа:

    1. Инициализация страницы с использованием метода PilotWeb3D.Initializer()
    2. Создание экземпляра PilotWeb3d и проверка, что у браузера есть поддержка WebGL

Пример кода для инициализации:

```Shell
var viewer;
var options = {
    env: '',
    api: '',
    getAccessToken: function(onTokenReady) {
        var token = 'YOUR_ACCESS_TOKEN';
        var timeInSeconds = 3600; // Use value provided by PilotWeb Authentication (OAuth) API
        onTokenReady(token, timeInSeconds);
    }
};
 
PilotWeb3.Initializer(options, function() {
 
    var htmlDiv = document.getElementById('pilotViewer');
    viewer = new Autodesk.Viewing.GuiViewer3D(htmlDiv);
    var startedCode = viewer.start();
    if (startedCode > 0) {
        console.error('Failed to create a Viewer: WebGL not supported.');
        return;
    }
 
    console.log('Initialization complete, loading a model next...');
 
});
```
---

## СОЗДАНИЕ ЭКЗЕМПЛЯРА PILOT-WEB-VIEWER

После инициализации компонентов можно создать экземпляр 2D или 3D просмотрщика Pilot-Web-Viewer.

Пример создания экземпляра 2D просмотрщика:

```Shell
	
htmlDiv = document.getElementById('pilotViewer');
viewer = new PilotWeb2D.CreateViewer(htmlDiv, {});

```

Пример создания экземпляра 3D просмотрщика:

```Shell
	
var htmlDiv = document.getElementById('pilotViewer');
viewer = new PilotWeb3D.CreateViewer(htmlDiv, {});

````

{{< hint type="note" icon=gdoc_github title="Примечание">}}
    Вызвать функцию viewer.start() необходимо только один раз.
{{< /highlight >}}

---

## ОСВОБОЖДЕНИЕ РЕСУРСОВ

После того, как просмотрщик больше не нужен на странице, его следует деинициализировать для освобождения ресурсов.

Пример кода для деинициализации:

```Shell	
viewer.finish();
viewer = null;
PilotWeb3D.shutdown();
```