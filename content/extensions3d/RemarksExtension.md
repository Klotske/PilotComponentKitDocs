---
title: "RemarksExtension"
draft: false
---

**RemarksExtension** -- расширение, которое позволяет задать точки замечаний на сцене. 
Замечания прикрепляются к графическим объектам на сцене, изменяя свое положение при изменении положения целевого объекта. 
Замечания рисуются на отдельном слое. Каждая точка замечания имеет статус -- опционально отображаемую текстуру.

Расширение имеет имя `PilotWeb3D.Remarks`.

Пример подключения в `html`:
```html
<script src="https://pilot.ascon.ru/componentkit/components/@VERSION@/extensions/Remarks3D/Remarks.min.js"></script>
```

Пример подключения в `javascript`:
```js
let htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
await viewer.start();
await viewer.extensionsLoader.loadExtension("PilotWeb3D.Remarks");
```

## Свойства

## get remarkManager(): RemarkManager
Возвращает менеджер точек замечаний.
Подробнее: [RemarkManager](#RemarkManager).
```js
public get remarkManager(): RemarkManager;
```

## Методы

### activate()
Метод включает расширение.
```js
activate(): void;
```
### deactivate()
Метод выключает расширение.
```js
deactivate(): void;
```

# RemarkManager {#RemarkManager}
**RemarkManager** -- менеджер замечаний, который предоставляет методы API для работы с точками замечаний.

```js

export class RemarkManager {

  readonly events: PilotWeb3D.IEventsDispatcher;
  readonly remarkSceneName = 'RemarkViewObjectScene';

  public get selectTargetElement(): boolean;
  public set selectTargetElement(value: boolean);

  public get placeRemarkOnClick(): boolean;
  public set placeRemarkOnClick(value: boolean);

  public get selectedRemarks(): RemarkViewObject[];
  public get selectedRemarksIds(): string[];

  public setActive(value: boolean): void;

  public getRemark(remarkId: string): RemarkViewObject | undefined;

  public addRemark(remarkParameters: RemarkObjectParameters, statusParameters?: RemarkStatusParameters): RemarkViewObject;

  public removeRemarks(remarkIds?: string[]): void;

  public select(remarkId: string | string[]): void;

  public deselect(remarkId: string | string[]): void;

  public setRemarkStatus(remarkId: string, statusParameters: RemarkStatusParameters): void;

  public setRemarksVisibility(visibiliity: boolean, remarkIds?: string[]): void;

  public setRemarksLayerVisibility(visibiliity: boolean): void;

}
```

## Поля

### remarkSceneName : string
Наименование слоя замечаний.
```js
readonly remarkSceneName = 'RemarkViewObjectScene';
```

### events : IEventsDispatcher
Диспетчер событий замечаний. Подробнее: [IEventsDispatcher](../../reference/EventsDispatcher).\
Список типов событий замечаний: [RemarkEventMap](#RemarkEventMap).
```js
  readonly events: PilotWeb3D.IEventsDispatcher;
```

## Свойства

### selectTargetElement : boolean {#selectTargetElement}
Включает или выключает режим выделения целевого объекта точки замечания. Если `true`, 
то выделение точки замечания приведет к выделению объекта, для которого добавлено замечание. 
```js
  get selectTargetElement(): boolean;
  set selectTargetElement(value: boolean);
```
По умолчанию: `false`.

### placeRemarkOnClick : boolean {#placeRemarkOnClick}
Включает или выключает режим размещения точек замечаний по клику на сцене. Если `true`, 
то клик по объекту на сцене приведёт к добавлению точки замечания для данного объекта в месте клика. 
После добавления точки замечания, либо при клике в пустую область, режим сбрасывается и свойство становится `false`.\
При смене режима размещения точек возникает событие [pilotRemarkPlacingModeChanged](#pilotRemarkPlacingModeChanged).
```js
  get placeRemarkOnClick(): boolean;
  set placeRemarkOnClick(value: boolean);
```
По умолчанию: `false`.

## selectedRemarks : RemarkViewObject[] {#selectedRemarks}
Возвращает выбранные объекты замечаний либо пустой массив, если ни одно замечание не выбрано.\
Подробнее: [RemarkViewObject](#RemarkViewObject).
```js
  get selectedRemarks(): RemarkViewObject[];
```
По умолчанию: `[]`.

##  Методы

### setActive()
Метод активирует или деактивирует менеджер точек замечаний.
```js
setActive(value: boolean): void;
```

### getRemark()
Метод возвращает объект замечания с указанным ID либо `undefined`, если объект с указанным ID не найден.
```js  
public getRemark(remarkId: string): RemarkViewObject | undefined;
```
где:\
`remarkId` -- идентификатор объекта замечания.

### addRemark()
Метод добавляет точку замечания на слой замечаний.
```js  
public addRemark(remarkParameters: RemarkObjectParameters, statusParameters?: RemarkStatusParameters): RemarkViewObject | null;
```

где:\
`remarkParameters` -- параметры точки замечания. Подробнее: [RemarkObjectParameters](#RemarkObjectParameters).

`statusParameters` -- параметры статуса замечания. Опциональный параметр. Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).

Возвращает добавленный на сцену объект замечания или `null`, если добавить точку не удалось. Подробнее: [RemarkViewObject](#RemarkViewObject).

### removeRemarks()
Метод удаляет точки замечаний и освобождает ресурсы, выделенные для удаляемых точек.
```js  
public removeRemarks(remarkIds?: string[]): void;
```
где:\
`remarkIds` -- идентификаторы точек замечаний для удаления. Опциональный параметр. Если не задан, то удаляются все добавленные на сцену точки замечаний.

### select()
Метод выделяет замечания на документе. 
При изменении списка селектированных замечаний возникает событие [pilotRemarkSelectionChanged](#pilotRemarkSelectionChanged).
```js  
select(remarkId: string | string[]): void;
```

где:\
`remarkId` -- идентификатор замечания или массив идентификаторов для выделения.

### deselect()
Метод снимает выделение замечаний на документе.
При изменении списка селектированных замечаний возникает событие [pilotRemarkSelectionChanged](#pilotRemarkSelectionChanged).
```js  
deselect(remarkId: string | string[]): void;
```

где:\
`remarkId` -- идентификатор замечания или массив идентификаторов для снятия выделения.

### clearSelection()
Метод снимает выделение с текущего выбранного замечания.
При изменении списка селектированных замечаний возникает событие [pilotRemarkSelectionChanged](#pilotRemarkSelectionChanged).
```js  
clearSelection(): void;
```

### setRemarkStatus()
Метод задает параметры статуса точки замечания.
```js  
public setRemarkStatus(remarkId: string, statusParameters: RemarkStatusParameters): void;
```

где:\
`remarkId` -- идентификатор точки замечания для обновления статуса.

`statusParameters` -- параметры статуса замечания. Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).

### setRemarksLayerVisibility()
Метод задает видимость слоя точек замечаний.
```js
public setRemarksLayerVisibility(visibiliity: boolean): void;
```
где:

`visibiliity` -- параметр видимости слоя замечаний. Если `true`, то слой замечаний отрисовывается в процессе рендера. 
В противном случае слой замечаний не рисуется, и объекты замечаний на сцене не показываются.


## RemarkEventMap {#RemarkEventMap}
События замечаний.
```js
interface RemarkEventMap {
  'pilotRemarkPlacingModeChanged' : Event;
  'pilotRemarkSelectionChanged' : PilotWeb3D.SelectionChangedEvent;
}
```
### pilotRemarkPlacingModeChanged {#pilotRemarkPlacingModeChanged}
```js
  'pilotRemarkPlacingModeChanged' : Event;
```
Событие возникает при изменении свойства [placeRemarkOnClick](#placeRemarkOnClick).

### pilotRemarkSelectionChanged {#pilotRemarkSelectionChanged}
```js
  'pilotRemarkSelectionChanged' : PilotWeb3D.SelectionChangedEvent; 
```
Событие возникает при изменении списка селектированных замечаний. Подробнее: [Events3D](../../reference3d/Events#Events3D).

# RemarkViewObject {#RemarkViewObject}
Графический объект, представляющий собой точку замечания. Добавляется на слой замечаний. Расширяет [ViewObject](../../reference3d/render/ViewObject).
```js
export class RemarkViewObject extends PilotWeb3D.ViewObject {
  constructor(remarkParamters?: RemarkObjectParameters, statusParameters?: RemarkStatusParameters);

  get remarkParameters(): RemarkObjectParameters;

  get statusParameters(): RemarkStatusParameters;

  updateRemark(parameters: RemarkObjectParameters): void;

  updateStatus(parameters: RemarkStatusParameters): void;
}
```

## Конструктор
```js
  constructor(remarkParamters?: RemarkObjectParameters, statusParameters?: RemarkStatusParameters);
```

где:\
`remarkParamters` -- опциональные параметры точки замечания. Если не заданы, то создается точка замечания со значениями по умолчанию. Подробнее: [RemarkObjectParameters](#RemarkObjectParameters).

`statusParameters` -- опциональные параметры статуса замечания. Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).

## Свойства

### remarkParameters() : RemarkObjectParameters
Возвращает текущие параметры замечания.
```js
  get remarkParameters(): RemarkObjectParameters;
```
Подробнее: [RemarkObjectParameters](#RemarkObjectParameters).

### statusParameters() : RemarkStatusParameters
Возвращает текущие параметры статуса замечания.
```js
  get statusParameters(): RemarkStatusParameters;
```
Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).

## Методы

### updateRemark()
Метод обновляет параметры точки замечания. Внутри `parameters` можно определять только изменившиеся параметры точки замечания. 
Например, для изменения размера точки достаточно передать `{ markSize : newSize }`. При этом позиция точки, иконка замечания и другие параметры останутся неизменными. Подробнее: [RemarkObjectParameters](#RemarkObjectParameters).
```js
  updateRemark(parameters: RemarkObjectParameters): void;
```

### updateStatus()
Метод обновляет параметры статуса точки замечания. Внутри `parameters` можно определять только изменившиеся параметры статуса. 
Например, для изменения размера статуса достаточно передать `{ statusSize : newSize }`. При этом смещение статуса, иконка статуса и другие параметры останутся неизменными. Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).
```js
  updateStatus(parameters: RemarkStatusParameters): void;
```

# RemarkObjectParameters {#RemarkObjectParameters}
Параметры точки замечания.
```js
export interface RemarkObjectParameters {
  remarkGuid?: string,
  targetModelGuid?: string,
  targetEntityGuid?: string,
  position?: Point3,
  relativePosition?: Point3,
  markSize?: { x: number, y: number },
  svgIcon?: string
}
```

### remarkGuid : string
Идентификатор точки замечания. Опциональный параметр. Если не задан, уникальный идентификатор генерируется автоматически.

### targetModelGuid : string
Идентификатор части модели, которой принадлежит целевой объект.\
Необязательный параметр, используется совместно с `targetEntityGuid`. Если не указан, то поиск целевого объекта выполняется по всем частям модели.\
Подробнее: [ModelElement.modelPartId](../../reference3d/modelelement/ModelElement#modelPartId).

### targetEntityGuid : string {#targetObject}
Идентификатор элемента модели, геометрия которого используется как целевой объект для привязки замечания.\
Подробнее: [ModelElement.id](../../reference3d/modelelement/ModelElement#id).

### position : Point3 {#remarkAbsPosition}
Координаты точки замечания в мировом пространстве. Опциональный параметр. Если координаты не заданы, но задан целевой объект ([targetEntityGuid](#targetObject)) 
и относительное положение точки замечания ([relativePosition](#remarkRelPosition)), 
то абсолютное положение точки замечания рассчитывается, исходя из этих параметров. 
В противном случае используется значение по умолчанию: `{ x: 0, y: 0, z: 0 }`. Подробнее: [Point3](../../reference3d/navigation/Point3).

### relativePosition : Point3 {#remarkRelPosition}
Координаты точки замечания относительно целевого объекта. Опциональный параметр. 
Относительные координаты применяются только в том случае, если задан целевой объект ([targetEntityGuid](#targetObject)) и не заданы абсолютные координаты ([position](#remarkAbsPosition)). 
В случае, если заданы и целевой объект, и абсолютные координаты, то относительные координаты будут рассчитаны, исходя из этих параметров. 
Подробнее: [Point3](../../reference3d/navigation/Point3).

### markSize : {x: number, y: number}
Размеры точки замечания. Опциональный параметр. Если не задан, то используются значения по умолчанию: `{ x: 25, y: 25 }`.

### svgIcon : string
Иконка точки замечания, строковое описание `svg`. Необязательный параметр.

# RemarkStatusParameters {#RemarkStatusParameters}
Параметры статуса точки замечания.
```js
export interface RemarkStatusParameters {
  visible?: boolean,
  mapColor?: PilotWeb3D.Color,
  statusSize?: { x: number, y: number },
  statusOffset?: { x: number, y: number },
  svgIcon?: string
}
```

### visible : boolean
Определяет видимость статуса замечания на сцене. Опциональный параметр. Если не задан, то используется значение по умолчанию: `false`.

### mapColor : PilotWeb3D.Color
Определяет цвет статуса замечания. Опциональный параметр. При отрисовке цвет текстуры замечания умножается на этот цвет. 
Если не задан, то используется значение по умолчанию: `new PilotWeb3D.Color(1, 1, 1, 1)`.\
Подробнее: [Color](../../reference3d/render/Color).

### statusSize : { x: number, y: number }
Определяет размеры текстуры статуса замечания в пикселях. Опциональный параметр. Если не задан, то используется значение по умолчанию: `{ x: 30, y: 30 }`.

### statusOffset : { x: number, y: number }
Определяет смещение текстуры статуса замечания относительно точки замечания. Опциональный параметр. Указывается в пикселях.
Если не задан, то используется значение по умолчанию: `{ x: 25, y: 25 }`.

### svgIcon : string
Иконка статуса замечания, строковое описание `svg`. Необязательный параметр.
