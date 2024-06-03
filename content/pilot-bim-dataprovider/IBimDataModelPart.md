---
title: IBimDataModelPart
draft: false
weight: 3
---

**IBimDataModelPart** - интерфейс объекта посредника для чтения и записи файлов модели.
Наследуется от [IBimDataPart](../IBimDataPart).

```js
export interface IBimDataModelPart extends IBimDataPart {
  update(buffer: ArrayBuffer): Promise<void>;
  getAllTessellations(): Promise<Map<string, BimDataTessellation>>;
  getTessellations(versionFrom: bigint, versionTo: bigint): Promise<Map<string, BimDataTessellation>>;
  getAllElements(): Promise<BimDataElement[]>;
  getElements(versionFrom: bigint, versionTo: bigint): Promise<BimDataElement[]>;
  getDiffElements(versionFrom: bigint, versionTo: bigint): Promise<BimDataElement[]>;
  getElementTessellations(versionFrom: bigint, versionTo: bigint): Promise<Map<string, BimDataTessellation>>;
  getElementProperties(elementId: string, version: bigint): Promise<BimDataElementPropertySet[]>;
  getAllVersions(): Promise<bigint[]>;
  getLatestVersion(): Promise<bigint>;
}
```

## Методы

### update()
Метод дополняет текущий файл модели новыми данными.
```js
  update(buffer: ArrayBuffer): Promise<void>;
```
где:\
`buffer` -- массив данных файла модели.

### getAllTessellations()
Метод возвращает список всех тесселляций элементов модели.
```js
  getAllTessellations(): Promise<Map<string, BimDataTessellation>>;
```
Возвращает словарь тесселяций, где ключом является уникальный идентификатор тесселляции. Подробнее: [BimDataTessellation](../BimDataClasses/#BimDataTessellation).

### getTessellations()
Метод возвращает тесселляции, версии которых находятся в указанном диапазоне. Если тесселяция имеет несколько версий, возвращается максимально возможная версия тесселляции в указанном диапазоне.
```js
  getTessellations(versionFrom: bigint, versionTo: bigint): Promise<Map<string, BimDataTessellation>>;
```
где:\
`versionFrom` -- начальное значение версии модели для поиска.\
`versionTo` -- конечное значение версии модели для поиска. Должно быть больше или равно `versionFrom`.\
Возвращает словарь тесселяций, где ключом является уникальный идентификатор тесселляции. Подробнее: [BimDataTessellation](../BimDataClasses/#BimDataTessellation).

### getAllElements()
Метод возвращает список всех элементов модели.
```js
  getAllElements(): Promise<BimDataElement[]>;
```
Возвращает список элементов модели. Подробнее: [BimDataElement](../BimDataClasses/#BimDataElement).

### getElements()
Метод возвращает элементы модели, версии которых находятся в указанном диапазоне. Если элемент имеет несколько версий, возвращается элемент максимально возможной версии в указанном диапазоне.
```js
  getElements(versionFrom: bigint, versionTo: bigint): Promise<BimDataElement[]>;
```
где:\
`versionFrom` -- начальное значение версии модели для поиска.\
`versionTo` -- конечное значение версии модели для поиска. Должно быть больше или равно `versionFrom`.\
Возвращает список элементов модели. Подробнее: [BimDataElement](../BimDataClasses/#BimDataElement).

### getDiffElements() {#getDiffElements}
Метод вычисляет разницу двух версий модели и возвращает список изменившихся элементов.
```js
  getDiffElements(versionFrom: bigint, versionTo: bigint): Promise<BimDataElement[]>;
```
где:\
`versionFrom` -- начальное значение версии модели для поиска.\
`versionTo` -- конечное значение версии модели для поиска. Может быть меньше `versionFrom`.\
Возвращает список изменившихся элементов модели. Подробнее: [BimDataElement](../BimDataClasses/#BimDataElement).\
Тип изменения элемента указан в свойстве `BimDataElement.objectState`. Подробнее: [BimDataNodeState](../BimDataClasses/#BimDataNodeState).

### getElementTessellations()
Метод возвращает тесселляции элементов модели, версии которых находятся в указанном диапазоне. Если элемент имеет несколько версий, возвращается тесселляция элемента максимально возможной версии (если диапазон задан в порядке возрастания) или минимально возможной версии (если диапазон задан в порядке убывания версий).\
Иными словами, метод возвращает тесселляции, необходимые для перестроения элементов модели при переключении версий с `versionFrom` на `versionTo`.
```js
  getElementTessellations(versionFrom: bigint, versionTo: bigint): Promise<Map<string, BimDataTessellation>>;
```
где:\
`versionFrom` -- начальное значение версии модели для поиска.\
`versionTo` -- конечное значение версии модели для поиска. Может быть меньше `versionFrom`.\
Возвращает словарь тесселяций, где ключом является уникальный идентификатор тесселляции. Подробнее: [BimDataTessellation](../BimDataClasses/#BimDataTessellation).

### getElementProperties()
Метод возвращает свойства элемента модели указанной версии.
```js
  getElementProperties(elementId: string, version: bigint): Promise<BimDataElementPropertySet[]>;
```
где:\
`elementId` -- идентификатор элемента модели.\
`version` -- версия модели.\
Возвращает список свойств элемента. Подробнее: [BimDataElementPropertySet](../BimDataClasses/#BimDataElementPropertySet).

### getAllVersions()
Метод возвращает список всех версий модели
```js
  getAllVersions(): Promise<bigint[]>;
```
Возвращает список версий модели.

### getLatestVersion()
Метод возвращает последнюю версию модели
```js
  getLatestVersion(): Promise<bigint>;
```
Возвращает последнюю версию модели.