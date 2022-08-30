---
title: "Сопоставление методов Autodesk Forge/Pilot-Web-Viewer/Pilot-BIM"
date: 2022-08-04T12:44:03+03:00
draft: false

---

## Сопоставление методов 3D API

{{< columns >}} <!-- begin columns block -->
### Название метода Autodesk Forge

<---> <!-- magic separator, between columns -->

### Название метода Pilot-Web-Viewer

<---> <!-- magic separator, between columns -->

### Название метода Pilot-BIM

<---> <!-- magic separator, between columns -->

### Комментарий

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`start(url, options, onSuccessCallback, onErrorCallback, initOptions): number`

<---> <!-- magic separator, between columns -->

`start(): number`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Подписка на события и др. действия (загрузка расширений — не реализовано)

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`finish(): void`

<---> <!-- magic separator, between columns -->

`finish(): void`
<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Отписка от событий (выгрузка расширений — не реализовано)

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`loadModel(url, options, onSuccessCallback, onErrorCallback): void`

<---> <!-- magic separator, between columns -->

`loadModel(buffer: ArrayBuffer, options: {}, onSuccessCallback: SuccessCallback, onErrorCallback: ErrorCallback): void`
<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Загрузка модели во вьювер

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`unloadModel(model): void`

<---> <!-- magic separator, between columns -->

`unloadModel(modelId: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Выгрузить модель (пока не   определились с параметрами)

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`GetAllModels(): Model[]`

<---> <!-- magic separator, between columns -->

`getAllModels(): ModelPart[]`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Получить все части модели

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getVisibleModels(): Model[]`

<---> <!-- magic separator, between columns -->

`getVisibleModels(): ModelPart[]`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Получить все видимые модели

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getHiddenModels(): Model[]`

<---> <!-- magic separator, between columns -->

`getHiddenModels(): ModelPart[]`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Получить скрытые модели

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hideModel(model: number | Model): boolean`

<---> <!-- magic separator, between columns -->

`hideModel(model: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Скрыть модель (часть модели)

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`showModel(model: string | Model,  preserveTools): boolean`

<---> <!-- magic separator, between columns -->

`showModel(model: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Показать ранее скрытую модель

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`getAggregateSelection(callback): Selection[]`

<---> <!-- magic separator, between columns -->

`getSelection(): Selection[]`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Получить селектированные объекты по моделям. У Forge есть 2 разных метода getSelection и getAggregateSelection.
Один работает для одной модели, второй для множества моделей. У нас всегда работаем с множестовм моделей.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hide(node: number[] | number, model?: Model): void`

<---> <!-- magic separator, between columns -->

`hide(elementIds: string[] | string, model?: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Спрятать отдельные бим-объекты (элементы) в модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hideAll(): void`

<---> <!-- magic separator, between columns -->

`hideAll(): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Спрятать все.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`show(node: number[] | number, model?: Model): void`

<---> <!-- magic separator, between columns -->

`show(elementIds: string[]|string, model?: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Показать отдельные бим-объекты (элементы) в модели.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`showAll(): void`

<---> <!-- magic separator, between columns -->

`showAll(): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Показать все.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`toggleSelect(dbid, model, selectionType): void`

<---> <!-- magic separator, between columns -->

`toggleSelect(elementIds: string[] | string, model?: string | ModelPart) : void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Сменить селект на элементах на противоположный. SelectType – тип выбора элемента (типа последний или корневой, у нас не реализовано).

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`select(dbids, model, selectionType): void`

<---> <!-- magic separator, between columns -->

`select(elementIds: string[] | string, model?: string | ModelPart) : void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Селектировать бим-объекты (элементы).

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`clearSelection(): void`

<---> <!-- magic separator, between columns -->

`clearSelection(): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Снять селектирование.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`setThemingColor(dbId, color, model, recursive): void`

<---> <!-- magic separator, between columns -->

`setColor(elementIds: string[] | string, color: THREE.Color, model?: string | ModelPart): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Задать цвет для бим-объектов (элементов).
Задаем как THREE.Color но этот цвет не позволяет задать альфа канал. Рекурсивность не реализована.

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`clearThemingColors(model): void`

<---> <!-- magic separator, between columns -->

`clearColors(model? : string | ModelPart): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Вернуть цвет для модели

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`addEventListener(type, listener, options)`

<---> <!-- magic separator, between columns -->

`events.addEventListener(type: string, listener: EventListener, options?: any): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Подписаться на событие. У Forge эти методы можно вызвать прям у viewer. У нас будет отдельное св-во events. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`dispatchEvent(event)`

<---> <!-- magic separator, between columns -->

`events.dispatchEvent(event: string | Event): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Отправить событие. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`hasEventListener(type, listener)`

<---> <!-- magic separator, between columns -->

`events.hasEventListener(type: string, listener: EventListener): boolean`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Проверить подписан или нет. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`removeEventListener(type, listener)`

<---> <!-- magic separator, between columns -->

`events.removeEventListener(type: string, listener: EventListener): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Отписаться. 

{{< /columns >}}

---

{{< columns >}} <!-- begin columns block -->

`clearListeners(): void`

<---> <!-- magic separator, between columns -->

`clearListeners(): void`

<---> <!-- magic separator, between columns -->

&nbsp;

<---> <!-- magic separator, between columns -->

Очистить подписки. 

{{< /columns >}}