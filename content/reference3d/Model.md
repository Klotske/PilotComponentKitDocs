---
title: "Model"
date: 2022-08-29T14:44:03+03:00
draft: false

---
**Model** -- это класс управления консолидированной моделью, загруженной в компонент.

## Методы

### getAllModelParts()
Метод возвращает все загруженные части консолидированной модели.
```js
getAllModelParts(): ModelPart[];
```

### getModelPart()
Метод возвращает часть консолидированной модели по её идентификатору.
```js
getModelPart(id: string): ModelPart;
```
где:\
`id` -- идентификатор части консолидированной модели.

### getVisibleModelParts()
Метод возвращает все видимые части консолидированной модели.
```js
getVisibleModelParts(): ModelPart[]
```

### getHiddenModelParts()
Метод возвращает все скрытые части консолидированной модели.
```js
getHiddenModelParts(): ModelPart[]
```

### hideModelPart()
Метод позволяет скрыть часть консолидированной модели.
```js
hideModelPart(modelPart: string | ModelPart): void;
```

где:\
`modelPart` -- идентификатор или экземпляр части модели.

### showModelPart()
Метод позволяет показать часть консолидированной модели.
```js
showModelPart(modelPart: string | ModelPart): void
```

где:\
`modelPart` -- идентификатор или экземпляр части модели.

### hide()
Метод позволяет скрыть элементы модели.
```js
hide(elementIds: string[] | string, modelPart?: string | ModelPart): void
```

где:\
`elementIds` -- один или несколько идентификаторов элементов модели.

`modelPart` -- идентификатор или экземпляр части модели. Необязательный параметр. Если этот параметр не задан, то обрабатываются элементы первой загруженной части модели.

### hideAll()
Метод позволяет скрыть все элементы и части модели.
```js
hideAll(): void;
```

### show()
Метод позволяет показать скрытые элементы.
```js
show(elementIds: string[] | string, modelPart?: string | ModelPart): void;
```

где:\
`elementIds` -- один или несколько идентификаторов элементов модели.

`modelPart` -- идентификатор или экземпляр части модели. Необязательный параметр. Если этот параметр не задан, то обрабатываются элементы первой загруженной части модели.

### showAll()
Метод позволяет показать все элементы и части модели.
```js
showAll(): void;
```

### isolate()
Метод позволяет изолировать элементы одной части модели. Все неизолированные элементы модели будут скрыты.
```js
isolate(elementIds: string[], modelPart: string | ModelPart): void;
```

где:\
`elementIds` -- один или несколько идентификаторов элементов модели.

`modelPart` -- идентификатор или экземпляр части модели. Необязательный параметр. Если этот параметр не задан, то обрабатываются элементы первой загруженной части модели.

### isolateMultiple()
Метод позволяет изолировать элементы модели. Все неизолированные элементы модели будут скрыты.
```js
isolateMultiple(elements: ModelElementIds[]): void;
```

где:\
`elements` -- список идентификаторов элементов модели, сгруппированных по части модели. Подробнее: [ModelElementIds](../modelelement/ModelElementIds).

### select()
Метод позволяет выделить элементы.
```js
select(elementIds: string[] | string, modelPart: string | ModelPart, selectionMode: SelectionMode): void
```

где:\
`elementIds` -- один или несколько идентификаторов элементов модели.

`modelPart` -- идентификатор или экземпляр части модели.

`selectionMode` -- режим выделения. Подробнее:  [SelectionMode](../SelectionMode).

### deselect()
Метод позволяет снять выделение с заданных элементов.
```js
deselect(elementIds: string[] | string, modelPart?: string | ModelPart): void
```

где:\
`elementIds` -- один или несколько идентификаторов элементов модели.

`modelPart` -- идентификатор или экземпляр части модели. Необязательный параметр. Если этот параметр не задан, то обрабатываются элементы первой загруженной части модели.

### clearSelection()
Метод позволяет снять выделение со всех элементов модели.
```js
clearSelection(): void;
```

### getSelection()
Метод позволяет получить выделенные элементы модели. Подробнее: [ModelElementIds](../modelelement/ModelElementIds).
```js
getSelection(): ModelElementIds[];
```

### getHiddenElements() {#getHiddenElements}
Метод позволяет получить все скрытые элементы. Подробнее: [ModelElementIds](../modelelement/ModelElementIds).
```js
getHiddenElements(): ModelElementIds[]
```

### getIsolatedElements()
Метод позволяет получить все изолированные элементы. Подробнее: [ModelElementIds](../modelelement/ModelElementIds).
```js
getIsolatedElements(): ModelElementIds[] 
```

### getVisibleElements()
Метод позволяет получить все видимые элементы. Подробнее: [ModelElementIds](../modelelement/ModelElementIds).
```js
getVisibleElements(): ModelElementIds[] 
```

### setColor()
Метод позволяет задать цвет элементов модели.
```js
setColor(elementIds: string[] | string, r: number, g: number, b: number, a: number, modelPart?: string | ModelPart): void
```

где:\
`elementIds` -- один или несколько идентификаторов элементов модели.

`modelPart` -- идентификатор или экземпляр части модели. Необязательный параметр. Если этот параметр не задан, то обрабатываются элементы первой загруженной части модели.

`r` -- красный цвет (0-255).

`g` -- зеленый цвет (0-255).

`b` -- синий цвет (0-255).

`a` -- альфа-канал (0-1).

### clearColors()
Метод позволяет восстановить все цвета для элементов модели.
```js
clearColors(model? : string | ModelPart): void;
```

где:\
`modelPart` -- идентификатор или экземпляр части модели. Необязательный параметр. Если этот параметр не задан, то обрабатывается первая загруженная часть модели.

### setGhostMode()
Метод задает призрачный режим отображения для скрытых объектов. В этом режиме скрытые объекты отображаются на сцене в полупрозрачном, бесцветном виде.
```js
setGhostMode(value: boolean): void;
```

где:\
`value` -- задаёт активность призрачного режима.

### getElementProperties() {#getElementProperties}
Метод позволяет получить свойства элемента.
```js
getElementProperties(elementId: string, modelPart?: string | ModelPart, version?: BigInt): ModelElementPropertySet[]
```

где:\
`elementId` -- идентификатор элемента.

`modelPart` -- идентификатор части модели или экземпляр части модели. Если этот параметр не задан, то обрабатывается первая загруженная часть модели.

`version` -- версия модели. Задается в тиках. Если версия не указана, то берутся свойства актуальной версии загруженной части модели.

Возвращает набор данных типа [ModelElementPropertySet](../modelelement/ModelElementPropertySet).


### canDelete() {#canDelete}
Метод проверяет, что переданные идентификаторы объектов соответствуют фильтрам объектов для удаления.
```js
  canDelete(elementIds: ModelElementIds[]): boolean;
```

где:\
`elementIds` -- идентификаторы объектов для проверки удаления. Подробнее: [ModelElementIds](../modelelement/ModelElementIds).

Возвращает `true`, если каждый из переданных идентификаторов соответствует хотя бы одному фильтру.

### delete() {#delete}
Метод вызывает [DELETE_OBJECTS_EVENT](../Events/#Events3D) с переданными идентификаторами объектов модели, если каждый идентификатор соответствует хотя бы одному фильтру.
```js
  delete(elementIds: ModelElementIds[]): boolean;
```

где:\
`elementIds` -- идентификаторы объектов для удаления. Подробнее: [ModelElementIds](../modelelement/ModelElementIds).

Возвращает `true`, если удалось вызвать [DELETE_OBJECTS_EVENT](../Events/#Events3D). В противном случае возвращается `false`.

### addDeletionFilter() {#addDeletionFilter}
Метод добавляет фильтр объектов для удаления.
```js
  addDeletionFilter(filter: DeleteEventFilter): void;
```

где:\
`filter` -- фильтр объектов для удаления. Подробнее: [DeleteEventFilter](#DeleteEventFilter).


### removeDeletionFilter()
Метод удаляет фильтр объектов для удаления.
```js
  removeDeletionFilter(filter: DeleteEventFilter): void;
```

где:\
`filter` -- фильтр объектов для удаления. Подробнее: [DeleteEventFilter](#DeleteEventFilter).


## DeleteEventFilter {#DeleteEventFilter}
Фильтр объектов для удаления. 
```js
interface DeleteEventFilter {
  (modelId: string, entityId: string): boolean;
}
```
где:\
`modelId` -- идентификатор модели.

`entityId` -- идентификатор элемента модели.

Возвращает `true` для объектов, которые можно удалить. В противном случае -- `false`.