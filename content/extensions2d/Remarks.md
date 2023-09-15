---
title: "RemarksExtension"
draft: false
weight: 1
---

**RemarksExtension** -- расширение которое позволяет задать точки замечаний на документе. Замечания рисуются на отдельном слое. Также, каждая точка замечания имеет статус - опционально отображемую `svg` иконку.

Расширение имеет имя `PilotWeb2D.Remarks`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/Remarks2D/Remarks.min.js"></script>
```

Пример подключения в `javascript`:
```js
const htmlDiv = document.getElementById('pilotViewer')
const configuration = new PilotWeb2D.Viewer2DConfiguration();
const viewer = PilotWeb2D.CreateViewer(htmlDiv, configuration);
await viewer.start();
// загружаем расширение и активируем его
const remarksExtension = await viewer.extensionsLoader.loadExtension("PilotWeb2D.Remarks");
remarksExtension.activate();

```

## Свойства

## get RemarksManager(): RemarksManager
Возвращает менеджер точек замечаний.
Подробнее: [RemarksManager](#RemarksManager).
```js
get RemarksManager(): RemarksManager;
```

## get layersManager(): RemarksLayerManager
Возвращает менеджер слоев для замечаний.
Подробнее: [RemarksLayerManager](#RemarksLayerManager).
```js
get layersManager(): RemarksLayerManager;
```

## Методы

### activate()
Метод включает расширение.
```js
activate(): boolean;
```
### deactivate()
Метод выключает расширение.
```js
deactivate(): boolean;
```

### getClickPage()
Метод получает страницу, по которой был произведен щелчек мыши. Подробнее: <a href="../../reference2d/DocumentPage">DocumentPage</a>.
```js
protected getClickPage(event: MouseEvent): PilotWeb2D.DocumentPage
```

### getClickPoint()
Метод получает координаты точки без учета масштаба страницы. Подробнее: <a href="../../reference2d/Point2">Point2</a>.
Чтобы получить точки в масштабе страницы необходимо координаты точки умножить на масштаб страницы.

```js
protected getClickPoint(event: MouseEvent, offsetX = 0, offsetY = 0): PilotWeb2D.Point2
```


# RemarksManager {#RemarksManager}
**RemarksManager** -- менеджер замечаний, который предоставляет методы API для работы с точками замечаний.

```js
class RemarksManager {
  setActive(value: boolean): void;
  getRemark(remarkId: string): Remark | undefined;
  addRemark(remarkParams: RemarkParameters, status?: RemarkStatus): Remark;
  removeRemarks(ids: string[]): boolean;
  select(remarkId: string): void;
  setStatus(remarkIs: string, status: RemarkStatus): boolean;
  setRemarksVisibility(visibility: boolean, remarkIds?: string[]): void;
}
```

##  Методы

### setActive()
Метод активирует или деактивирует менеджер точек замечаний.
```js
setActive(value: boolean): void;
```

### getRemark()
Метод возвращает объект замечания с указанным идентификатором либо `undefined`, если объект не найден. Подробнее [Remark](#Remark)
```js  
getRemark(remarkId: string): Remark | undefined;
```
где:\
`remarkId` -- идентификатор замечания.

### addRemark()
Метод добавляет точку замечания на слой замечаний.
```js  
addRemark(remarkParams: RemarkParameters, status?: RemarkStatus): Remark
```
где:\
`remarkParams` -- параметры точки замечания. Подробнее: [RemarkParameters](#RemarkParameters).\
`status` -- параметры статуса замечания, опциональный параметр. Подробнее: [RemarkStatus](#RemarkStatus).\
Возвращает добавленный на документ объект замечания. Подробнее: [Remark](#Remark).

### removeRemarks()
Метод удаляет точки замечаний.
```js  
removeRemarks(ids: string[]): boolean;
```
где:\
`ids` -- идентификаторы точек замечаний для удаления, опциональный параметр. Если не задан, то удаляются все добавленные на сцену точки замечаний.

### select()
Метод управляет селектированием точек замечаний. Выбранное замечание может быть только одно.\
При вызове метода `select` выбирается замечание, идентификатор которого был передан как аргумент, а предыдущий выбор сбрасывается. Если замечание с нужным идентификатором не найдено, либо `remarkId` неопределён, то выбор также сбрасывается.
```js  
select(remarkId: string): void;
```
где:\
`remarkId` -- идентификатор точки замечания для выбора.

### setStatus()
Метод задает параметры статуса точки замечания.
```js  
setStatus(remarkId: string, status: RemarkStatus): boolean
```
где:\
`remarkId` -- идентификатор точки замечания для обновления статуса.\
`status` -- параметры статуса замечания. Подробнее: [RemarkStatus](#RemarkStatus).

### setRemarksVisibility()
Метод задает видимость точек замечаний.
```js
setRemarksVisibility(visibility: boolean, remarkIds: string[]): void
```
где:\
`visibiliity` -- параметр видимости замечаний.
`remarkIds` -- идентификаторы замечаний.


# RemarksLayerManager {#RemarksLayerManager}
**RemarksLayerManager** -- менеджер слоев для замечаний.

```js
class RemarksLayerManager {
  createLayer(): void;
  getLayer(pageNumber?: number): PilotWeb2D.ILayer;
  removeLayer(): boolean;
}
```

##  Методы

### createLayer
Создает новый слой.
```js
  createLayer(): void;
```

### getLayer
Получает слой для замечаний.
```js
  getLayer(pageNumber?: number): PilotWeb2D.ILayer
```
где:\
`page` -- номер страницы.
Метод возвращает объект описывающий слой. Подробнее: <a href="../../reference2d/ILayer">ILayer</a>.

### removeLayer
Удаляет слой для замечаний со всех страниц.
```js
  createLayer(): void;
```


# Remark {#Remark}
Объект представляющий точку замечания, добавляется на слой замечаний.
```js
class Remark {
  id: string;                       
  pageNumber: number;               
  container: RemarkHtmlContainer;   
  positionX: number;                
  positionY: number;                
  type?: string;                    
}
```

### id : string
Поле содержит идентификатор замечания

### pageNumber: number
Поле содержит номер страницы, на которой размещено замечание.

### container: RemarkHtmlContainer
Поле содержит объект с описанием HTML-элементов к замечанию. Подробнее: [RemarkHtmlContainer](#RemarkHtmlContainer).

### positionX: number
Поле содержит позицию по оси x на документе.

### positionY: number
Поле содержит позицию по оси y на документе.

### type: string
Поле содержит дополнительные параметры для идентификации замечания.

# RemarkHtmlContainer {#RemarkHtmlContainer}
Объект представляющий описание HTML-элементов к замечанию.
```js
class RemarkHtmlContainer {
  containerHtmlElement: HTMLElement;
  remarkHtmlElement: HTMLElement;
  statusHtmlElement: HTMLElement;
}
```

### containerHtmlElement: HTMLElement
Поле содержит HTML-контейнер для всего замечания.

### remarkHtmlElement: HTMLElement
Поле содержит HTML-контейнер для точки замечания.

### statusHtmlElement: HTMLElement
Поле содержит HTML-контейнер для статуса замечания.


# RemarkParameters {#RemarkParameters}
Параметры точки замечания.
```js
interface RemarkParameters {
  id: string;
  positionX: number;
  positionY: number;
  htmlElement?: HTMLElement | string;
  pageNumber?: number;
  containerClass?: string;
  mark?: string;
  type?: string;
}
```

### id: string
Идентификатор замечания.

### positionX: number
Позиция по оси x на документе.

### positionY: number
Позиция по оси y на документе.

### htmlElement: HTMLElement | string
Описание замечания в виде HTML-элементов или строковое описание `svg`. Параметр не обязательный. Если этот параметр не задан, то замечание будет отрисовываться стилем по умолчанию.

### pageNumber: number
Номер страницы, на которой необходимо разместить замечание. Параметр не обязательный. Если этот параметр не задан, то замечание разместится на первой странице.

### containerClass: string
Имя `css` класса, который будет применен к общему контейнеру замечания. Параметр не обязательный.

### mark: string
Метка на замечании. Параметр не обязательный.

### type: string
Дополнительные параметры описания замечания. Параметр не обязательный.

# RemarkStatus {#RemarkStatus}
Параметры статуса точки замечания.
```js
interface RemarkStatus {
  visible?: boolean;
  statusOffsetX?: number;
  statusOffsetY?: number;
  htmlElement?: HTMLElement | string;  
}
```

### visible: boolean
Определяет видимость статуса замечания, опциональный параметр. Если не задан, то используется значение по умолчанию: `false`.

### statusOffsetX: number
Смещение статуса по оси x от центра точки замечания. Параметр не обязательный.

### statusOffsetY: number
Смещение статуса по оси y от центра точки замечания. Параметр не обязательный.

### htmlElement: HTMLElement | string
Описание замечания в виде HTML-элементов или строковое описание `svg`. Параметр не обязательный. 
