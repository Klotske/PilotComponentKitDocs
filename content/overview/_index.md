---
title: "Обзор"
date: 2022-08-26T14:44:03+03:00
draft: false
weight: 0
resources:
- name: 3d_view
  src: "3d_viewer.png"
  title: BIM-модель
  params:
      credits: "Некоторые инструменты специфичны только для BIM-моделей. Например, для удобства навигации по BIM-модели вы можете использовать **видовой куб**, расположенный в верхней части страницы."
- name: 2d_view
  src: "2d_viewer.png"
  title: XPS-документ
  params:
      credits: "Для удобного просмотра документов на панели инструментов есть специальные команды."
---

**PilotWeb3D**, **PilotBimDataProvider** и **PilotWeb2D** -- это компоненты Pilot-Cloud. Они включают в себя библиотеки JavaScript, стили, методы API и документацию,
интегрируются в любой веб-сайт, портал или мобильное приложение. 
С помощью этих компонентов решаются задачи отображения в браузерах информационных моделей (BIM) и документов, навигации по ним, работы с данными трёхмерных моделей,
в том числе скрытия элементов модели, изменения их цвета, получения свойств, выполнения измерений. 

#### Информационные модели

Для загрузки моделей в компоненты **PilotWeb3D** и **PilotBimDataProvider** используются файлы **.bm**, формируемые сервисом **Pilot-BIM-Server**. Файлы **.bm** -- 
это контейнер данных информационной модели.
Он может содержать как изменение данных относительно предыдущей версии, так и актуальное состояние модели, включающее все её изменения до необходимой версии.

<iframe height="580px" width="100%" style="box-sizing: border-box; border: 0px;" src="https://stackblitz.com/edit/web-platform-v9kotm?embed=1&file=index.html&hideDevTools=1&hideExplorer=1&hideNavigation=1&theme=light&view=preview"></iframe>


#### Документы

Для загрузки документов используйте файлы в формате **.xps** (Open XML Paper Specification, ECMA-388).

<iframe height="580px" width="100%" style="box-sizing: border-box; border: 0px;" src="https://stackblitz.com/edit/web-platform-icnnur?embed=1&file=index.html&hideDevTools=1&hideExplorer=1&hideNavigation=1&theme=light&view=preview"></iframe>

