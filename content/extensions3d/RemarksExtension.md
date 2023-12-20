---
title: "RemarksExtension"
draft: false
---

**RemarksExtension** -- расширение, которое позволяет задать точки замечаний на сцене. 
Замечания прикрепляются к графическим объектам на сцене, изменяя свое положение при изменении положения целевого объекта. 
Замечания рисуются на отдельном слое. Также каждая точка замечания имеет статус -- опционально отображаемую текстуру.

Расширение имеет имя `PilotWeb3D.Remarks`.

Пример подключения в `html`:
```html
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/Remarks3D/Remarks.min.js"></script>
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
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

  public get placeRemarkOnClick(): boolean;
  public set placeRemarkOnClick(value: boolean);

  public get selectedRemarks(): RemarkViewObject[];

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

### placeRemarkOnClick : boolean {#placeRemarkOnClick}
Включает или выключает режим размещения точек замечаний по клику на сцене. Если `true`, 
то клик по объекту на сцене приведёт к добавлению точки замечания для данного объекта в месте клика. 
После добавления точки замечания, либо при клике в пустую область, режим сбрасывается и свойство становится `false`.\
Также при смене режима размещения точек возникает событие [remarkPlacingModeChanged](#remarkPlacingModeChanged).
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

`statusParameters` -- параметры статуса замечания. Опциональный параметр. Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).\
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
```js  
select(remarkId: string | string[]): void;
```

где:\
`remarkId` -- идентификатор замечания или массив идентификаторов для выделения.

### deselect()
Метод снимает выделение замечаний на документе.
```js  
deselect(remarkId: string | string[]): void;
```

где:\
`remarkId` -- идентификатор замечания или массив идентификаторов для снятия выделения.

### clearSelection()
Метод снимает выделение с текущего выбранного замечания.
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
В противном случае слой замечаний не рисуется и объекты замечаний на сцене не показываются.


## RemarkEventMap {#RemarkEventMap}
События замечаний.
```js
interface RemarkEventMap {
  'remarkPlacingModeChanged' : Event;
  'remarkClicked' : PilotWeb3D.ClickedEvent;
}
```
### remarkPlacingModeChanged {#remarkPlacingModeChanged}
```js
  'remarkPlacingModeChanged' : Event;
```
Событие возникает при изменении свойства [placeRemarkOnClick](#placeRemarkOnClick).

### remarkClicked
```js
  'remarkClicked' : PilotWeb3D.ClickedEvent; 
```
Событие возникает при клике по точке замечания. Подробнее: [Events3D](../../reference3d/Events#Events3D).

# RemarkViewObject {#RemarkViewObject}
Графический объект, представляющий точку замечания. Добавляется на слой замечаний. Расширяет [ViewObject](../../reference3d/render/ViewObject).
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
`remarkParamters` -- параметры точки замечания, опциональный параметр. Если не заданы, то создается точка замечания со значениями по умолчанию. Подробнее: [RemarkObjectParameters](#RemarkObjectParameters).

`statusParameters` -- параметры статуса замечания, опциональный параметр. Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).

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
Метод обновляет параметры точки замечания. Допустимо определять внутри `parameters` только изменившиеся параметры точки замечания. Например, для изменения размера точки достаточно передать `{ pointSize : newSize }`, при этом позиция точки, её цвет, геометрия и другие параметры останутся неизменными. Подробнее: [RemarkObjectParameters](#RemarkObjectParameters).
```js
  updateRemark(parameters: RemarkObjectParameters): void;
```

### updateStatus()
Метод обновляет параметры статуса точки замечания. Допустимо определять внутри `parameters` только изменившиеся параметры статуса. 
Например, для изменения размера статуса достаточно передать `{ statusSize : newSize }`, при этом смещение статуса, цвет, текстура и другие параметры останутся неизменными. Подробнее: [RemarkStatusParameters](#RemarkStatusParameters).
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
  position?: THREE.Vector3,
  relativePosition?: THREE.Vector3,
  pointSize?: number,
  rimSize?: number,
  defaultPointColor?: PilotWeb3D.Color,
  defaultRimColor?: PilotWeb3D.Color,
  hoveredPointColor?: PilotWeb3D.Color,
  hoveredRimColor?: PilotWeb3D.Color,
  selectedPointColor?: PilotWeb3D.Color,
  selectedRimColor?: PilotWeb3D.Color,
  pointGeometry?: THREE.InstancedBufferGeometry,
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

### position : THREE.Vector3 {#remarkAbsPosition}
Координаты точки замечания в мировом пространстве. Опциональный параметр. Если координаты не заданы, но задан целевой объект ([targetEntityGuid](#targetObject)) 
и относительное положение точки замечания ([relativePosition](#remarkRelPosition)), 
то абсолютное положение точки замечания рассчитывается, исходя из этих параметров. 
В противном случае используется значение по умолчанию: `new THREE.Vector3(0, 0, 0)`. Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

### relativePosition : THREE.Vector3 {#remarkRelPosition}
Координаты точки замечания относительно целевого объекта. Опциональный параметр. 
Относительные координаты применяются только в том случае, если задан целевой объект ([targetEntityGuid](#targetObject)) и не заданы абсолютные координаты ([position](#remarkAbsPosition)). 
В случае, если заданы и целевой объект, и абсолютные координаты, то относительные координаты будут рассчитаны, исходя из этих параметров. 
Подробнее: [THREE.Vector3](https://threejs.org/docs/#api/en/math/Vector3).

### pointSize : number
Размер точки замечания без учета границы в пикселях. Опциональный параметр. Если не задан, то используется значение по умолчанию: `15`.\
При использовании геометрии по умолчанию `pointSize` будет задавать диаметр точки без учета границы.

### rimSize : number
Размер границы точки замечания в пикселях. Опциональный параметр. Если не задан, то используется значение по умолчанию: `3`.\
При использовании геометрии по умолчанию итоговый диаметр точки будет равен: `pointSize + 2 * rimSize`.

### defaultPointColor : PilotWeb3D.Color
Базовый цвет точки замечания. Опциональный параметр. Если не задан, то используется цвет по умолчанию: `#ffffffff`.\
Подробнее: [Color](../../reference3d/render/Color).

### defaultRimColor : PilotWeb3D.Color
Базовый цвет границы точки замечания. Опциональный параметр. Если не задан, то используется цвет по умолчанию: `#646464ff`.\
Подробнее: [Color](../../reference3d/render/Color).

### hoveredPointColor : PilotWeb3D.Color
Цвет точки замечания под действием ховера. Опциональный параметр. Если не задан, то используется цвет по умолчанию: `#c8c864ff`.\
Подробнее: [Color](../../reference3d/render/Color).

### hoveredRimColor : PilotWeb3D.Color
Цвет границы точки замечания под действием ховера. Опциональный параметр. Если не задан, то используется цвет по умолчанию: `#c8c864ff`.\
Подробнее: [Color](../../reference3d/render/Color).

### selectedPointColor : PilotWeb3D.Color
Цвет выбранной точки замечания. Опциональный параметр. Если не задан, то используется цвет по умолчанию: `#d3b268ff`.\
Подробнее: [Color](../../reference3d/render/Color).

### selectedRimColor : PilotWeb3D.Color
Цвет границы выбранной точки замечания. Опциональный параметр. Если не задан, то используется цвет по умолчанию: `#c89e3fff`.\
Подробнее: [Color](../../reference3d/render/Color).

### pointGeometry : THREE.InstancedBufferGeometry
Геометрия, используемая для отрисовки точки. По умолчанию используется геометрия круга.\
Подробнее: [THREE.InstancedBufferGeometry](https://threejs.org/docs/#api/en/core/InstancedBufferGeometry).


# RemarkStatusParameters {#RemarkStatusParameters}
Параметры статуса точки замечания.
```js
export interface RemarkStatusParameters {
  visible?: boolean,
  mapColor?: PilotWeb3D.Color,
  statusSize?: number,
  statusOffset?: THREE.Vector2,
  statusTexture?: THREE.Texture
}
```

### visible : boolean
Определяет видимость статуса замечания на сцене. Опциональный параметр. Если не задан, то используется значение по умолчанию: `false`.

### mapColor : PilotWeb3D.Color
Определяет цвет статуса замечания. Опциональный параметр. При отрисовке цвет текстуры замечания умножается на этот цвет. 
Если не задан, то используется значение по умолчанию: `new PilotWeb3D.Color(1, 1, 1, 1)`.\
Подробнее: [Color](../../reference3d/render/Color).

### statusSize : THREE.Vector2
Определяет размеры текстуры статуса замечания в пикселях. Опциональный параметр. Если не задан, то используется значение по умолчанию: `new THREE.Vector2(30, 30)`.

### statusOffset : THREE.Vector2
Определяет смещение текстуры статуса замечания относительно точки замечания. Опциональный параметр. Указывается в пикселях.\
Если не задан, то используется значение по умолчанию: `new THREE.Vector2(25, 25)`.\
Подробнее: [THREE.Vector2](https://threejs.org/docs/#api/en/math/Vector2).

### statusTexture : THREE.Texture
Текстура статуса замечания. Опциональный параметр.\
Подробнее: [THREE.Texture](https://threejs.org/docs/#api/en/textures/Texture).
