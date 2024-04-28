---

date: 2022-08-04T12:44:03+03:00
draft: false
---

# Pilot-ComponentKit

— это облачная платформа для создания индивидуальных BIM-решений на любом этапе жизненного цикла объекта капитального строительства от проектирования до эксплуатации.

Pilot-ComponentKit функционирует как PaaS (платформа как сервис), предоставляя компоненты для работы с BIM-моделью и XPS-документами.
Используя компоненты системы, такие как комплекс сервисов и API, вы можете разрабатывать собственные инженерные решения.

**PilotWeb3D**, **PilotBimDataProvider** и **PilotWeb2D** -- это компоненты Pilot-ComponentKit. Они включают в себя библиотеки JavaScript, стили, методы API и документацию,
интегрируются в любой веб-сайт, портал или мобильное приложение. 
С помощью этих компонентов решаются задачи отображения в браузерах информационных моделей (BIM) и документов, навигации по ним, работы с данными трёхмерных моделей,
в том числе скрытия элементов модели, изменения их цвета, получения свойств, выполнения измерений. 

### Информационные модели

Для загрузки моделей в компоненты **PilotWeb3D** и **PilotBimDataProvider** используются файлы **.bm**, формируемые сервисом **<a href="https://help.pilotems.com/ru/Content/p-BIM_obschie_svedeniya.htm">Pilot-BIM-Server</a>**. Файлы **.bm** -- 
это контейнер данных информационной модели.
Он может содержать как изменение данных относительно предыдущей версии, так и актуальное состояние модели, включающее все её изменения до необходимой версии.

<iframe height="580px" width="100%" style="box-sizing: border-box; border: 0px;" src="https://stackblitz.com/edit/typescript-t5zkkb?embed=1&file=index.ts&hideNavigation=1&theme=light&view=preview"></iframe>


### Документы

Для загрузки документов используйте файлы в формате **.xps** (Open XML Paper Specification, ECMA-388).

<iframe height="580px" width="100%" style="box-sizing: border-box; border: 0px;" src="https://stackblitz.com/edit/typescript-uzdwhd?embed=1&file=index.ts&hideNavigation=1&theme=light&view=preview"></iframe>

{{< hint type="important" icon=gdoc_error_outline title="Важно">}}
Стоимость ПО рассчитывается индивидуально. Просим обращаться в <a href="https://pilotems.com/ru/contacts/offices/">офисы АСКОН или партнёров</a>.
{{< /hint >}}










