---
title: "Сопоставление методов Autodesk Forge и PilotWeb3D"
date: 2022-08-04T12:44:03+03:00
draft: false
weight: 12
---

## Сопоставление методов 3D API

{{< columns >}} <!-- begin columns block -->
### Название метода Autodesk Forge

<---> <!-- magic separator, between columns -->

### Название метода PilotWeb3D

<---> <!-- magic separator, between columns -->

### Комментарий

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

#### Класс Viewer3D

<---> <!-- magic separator, between columns -->

#### Класс Viewer3D

<---> <!-- magic separator, between columns -->

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`start(url, options, onSuccessCallback, onErrorCallback, initOptions): number`

<---> <!-- magic separator, between columns -->

`start(): Promise<number>`

<---> <!-- magic separator, between columns -->

Подписка на события и др. действия.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`finish(): void`

<---> <!-- magic separator, between columns -->

`finish(): Promise<void>`

<---> <!-- magic separator, between columns -->

Отписка от событий.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`loadModel(url, options, onSuccessCallback, onErrorCallback): void`

<---> <!-- magic separator, between columns -->

`loadModelpart(buffer: ArrayBuffer, options: {}): Promise<void>`

<---> <!-- magic separator, between columns -->

Загрузка части модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`unloadModel(model): void`

<---> <!-- magic separator, between columns -->

`unloadModelPart(modelPart: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

Выгрузить часть модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`applyCamera(camera, fit)`

<---> <!-- magic separator, between columns -->

`setCameraParameters(params: CameraParameters): void`

<---> <!-- magic separator, between columns -->

Задать параметры камеры.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getCamera()`

<---> <!-- magic separator, between columns -->

`getCameraParameters(): CameraParameters`

<---> <!-- magic separator, between columns -->

Получить параметры камеры.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getScreenShot(w, h, cb, overlayRenderer): DOMString`

<---> <!-- magic separator, between columns -->

`makeScreenshot(mimeType?: string, quality?: number): Promise<Blob>`

<---> <!-- magic separator, between columns -->

Получить снимок экрана.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`GetAllModels(): Model[]`

<---> <!-- magic separator, between columns -->

`model.getAllModelParts(): ModelPart[]`

<---> <!-- magic separator, between columns -->

Получить все части модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getVisibleModels(): Model[]`

<---> <!-- magic separator, between columns -->

`model.getVisibleModelParts(): ModelPart[]`

<---> <!-- magic separator, between columns -->

Получить все видимые части модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getHiddenModels(): Model[]`

<---> <!-- magic separator, between columns -->

`model.getHiddenModels(): ModelPart[]`

<---> <!-- magic separator, between columns -->

Получить скрытые части модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`model.getVisibleElements(): ModelElement[]`

<---> <!-- magic separator, between columns -->

Получить все видимые элементы модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getHiddenNodes(model)`

<---> <!-- magic separator, between columns -->

`model.getHiddenElements(): ModelElement[]`

<---> <!-- magic separator, between columns -->

Получить все скрытые элементы модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hideModel(model: number | Model): boolean`

<---> <!-- magic separator, between columns -->

`model.hideModelPart(modelPart: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

Скрыть часть модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`showModel(model: string | Model,  preserveTools): boolean`

<---> <!-- magic separator, between columns -->

`model.showModelPart(modelPart: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

Показать ранее скрытую часть модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getAggregateSelection(callback): Selection[]`

<---> <!-- magic separator, between columns -->

`model.getSelection(): ModelElementIds[]`

<---> <!-- magic separator, between columns -->

Получить выделенные элементы. Работает для множества частей модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hide(node: number[] | number, model?: Model): void`

<---> <!-- magic separator, between columns -->

`model.hide(elementIds: string[] | string, modelPart?: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

Спрятать отдельные элементы в модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hideAll(): void`

<---> <!-- magic separator, between columns -->

`model.hideAll(): void`

<---> <!-- magic separator, between columns -->

Спрятать все.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`show(node: number[] | number, model?: Model): void`

<---> <!-- magic separator, between columns -->

`model.show(elementIds: string[]|string, modelPart?: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

Показать отдельные элементы в модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`showAll(): void`

<---> <!-- magic separator, between columns -->

`model.showAll(): void`

<---> <!-- magic separator, between columns -->

Показать все.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`select(dbids, model, selectionType): void`

<---> <!-- magic separator, between columns -->

`model.select(elementIds: string[] | string, modelPart?: string | ModelPart) : void`

<---> <!-- magic separator, between columns -->

Выделить элементы.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`model.deselect(elementIds: string[] | string, modelPart?: string | ModelPart) : void`

<---> <!-- magic separator, between columns -->

Снять выделение указанных элементов.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`clearSelection(): void`

<---> <!-- magic separator, between columns -->

`model.clearSelection(): void`

<---> <!-- magic separator, between columns -->

Снять выделение со всех моделей.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`setThemingColor(dbId, color, model, recursive): void`

<---> <!-- magic separator, between columns -->

`model.setColor(elementIds: string[] | string, r: number, g: number, b: number, a: number, modelPart?: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

Задать цвет для элементов.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`clearThemingColors(model): void`

<---> <!-- magic separator, between columns -->

`model.clearColors(modelPart? : string | ModelPart): void`

<---> <!-- magic separator, between columns -->

Вернуть цвет для всех элементов части модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`addEventListener(type, listener, options)`

<---> <!-- magic separator, between columns -->

`events.addEventListener(type: string, listener: EventListener, options?: any): void`

<---> <!-- magic separator, between columns -->

Подписаться на события.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`dispatchEvent(event)`

<---> <!-- magic separator, between columns -->

`events.dispatchEvent(event: string | Event): void`

<---> <!-- magic separator, between columns -->

Отправить событие. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hasEventListener(type, listener)`

<---> <!-- magic separator, between columns -->

`events.hasEventListener(type: string, listener: EventListener): boolean`

<---> <!-- magic separator, between columns -->

Проверить, подписан или нет. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`removeEventListener(type, listener)`

<---> <!-- magic separator, between columns -->

`events.removeEventListener(type: string, listener: EventListener): void`

<---> <!-- magic separator, between columns -->

Отписаться. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`clearListeners(): void`

<---> <!-- magic separator, between columns -->

`events.clearListeners(): void`
<---> <!-- magic separator, between columns -->

Очистить подписки. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

#### Класс BubbleNode

<---> <!-- magic separator, between columns -->

#### Класс ModelElement

<---> <!-- magic separator, between columns -->

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`get id(): string`

<---> <!-- magic separator, between columns -->

Получить идентификатор элемента модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`get parent(): ModelElement | undefined`

<---> <!-- magic separator, between columns -->

Получить родителя элемента модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`type(): string`

<---> <!-- magic separator, between columns -->

`get type(): string`

<---> <!-- magic separator, between columns -->

Получить тип элемента модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`name(): string`

<---> <!-- magic separator, between columns -->

`get name(): string`

<---> <!-- magic separator, between columns -->

Получить имя элемента модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`get children(): ModelElement[]`

<---> <!-- magic separator, between columns -->

Получить дочерние элементы.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

#### Класс InstanceTree

<---> <!-- magic separator, between columns -->

#### Класс ModelElementTree

<---> <!-- magic separator, between columns -->

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getRootId(): number`

<---> <!-- magic separator, between columns -->

`getRootElement(): ModelElement`

<---> <!-- magic separator, between columns -->

Получить корневой элемент дерева.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`getAllElements(): ModelElement[]`

<---> <!-- magic separator, between columns -->

Получить все элементы дерева списком.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`isDetachedElement(element: string | ModelElement): boolean`

<---> <!-- magic separator, between columns -->

Проверить, находится ли элемент вне дерева.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

отсутствует

<---> <!-- magic separator, between columns -->

`getChildLevelNumber(element: string | ModelElement): number`

<---> <!-- magic separator, between columns -->

Получить уровень вложенности для элемента.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`enumNodeChildren(node, callback, recursive): void`

<---> <!-- magic separator, between columns -->

`enumElementChildren(element: string | ModelElement, callback: (guid: string) => void, recursive?: boolean): void `

<---> <!-- magic separator, between columns -->

Применить действие ко всем дочерним элементам.

{{< /columns >}}

---