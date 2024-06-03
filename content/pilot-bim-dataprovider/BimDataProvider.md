---
title: "BimDataProvider"
draft: false

---
**BimDataProvider** -- основной класс компонента.

```js
class BimDataProvider {
  init(): Promise<void>;
  openModelPart(id: string, buffer: ArrayBuffer): Promise<IBimDataModelPart | undefined>;
  openCloudPart(id: string, buffer: ArrayBuffer): Promise<IBimDataCloudPart | undefined>;
  dispose(): Promise<void>;
  flushMemory(): Promise<void>;
}
```


## Методы

### init()
Метод инициализирует компонент.
```js
  init(): Promise<void>;
```

### openModelPart()
Метод открывает файл модели для чтения и записи.
```js
  openModelPart(id: string, buffer: ArrayBuffer): Promise<IBimDataModelPart | undefined>;
```
где:\
`id` -- уникальный идентификатор файла модели.\
`buffer` -- массив данных файла модели.\
Возвращает объект посредник для чтения или записи файла модели, если удалось открыть файл. Подробнее: [IBimDataModelPart](../IBimDataModelPart).
В противном случае возвращает `undefined`.

### openCloudPart()
Метод открывает файл облака точек для чтения.
```js
  openCloudPart(id: string, buffer: ArrayBuffer): Promise<IBimDataCloudPart | undefined>;
```
где:\
`id` -- уникальный идентификатор файла облака точек.\
`buffer` -- массив данных файла облака точек.\
Возвращает объект посредник для чтения файла облака точек, если удалось открыть файл. Подробнее: [IBimDataCloudPart](../IBimDataCloudPart).
В противном случае возвращает `undefined`.

### dispose()
Метод завершает работу компонента и освобождает выделенные ресурсы.
```js
  dispose(): Promise<void>;
```
{{< hint type="important" title="Важно">}}
После завершения работы компонента, чтение файлов модели и облаков точек через объекты посредники невозможно.
{{< /hint >}}

### flushMemory()
Метод освобождает память, выделенную компонентом, без завершения работы компонента.
```js
  flushMemory(): Promise<void>;
```
{{< hint type="important" title="Важно">}}
Метод не должен вызываться одновременно с чтением или записью файлов модели или облаков точек через объекты посредники.
{{< /hint >}}


## Пример использования
```js
import { BimDataBigIntMaxValue, BimDataProvider } from "@pilotdev/pilot-bim-dataprovider";

// Создаем и инициализируем компонент
const bimDataProvider = new BimDataProvider();
await bimDataProvider.init();

// Получаем объект посредник для чтения .bm файла
const modelPart = await bimDataProvider.openModelPart("uniqueModePartId", bmFileBuffer);

// Получаем список всех элементов части модели.
const elements = await modelPart.getAllElements();

// Получаем список всех тесселляций объектов модели
const tesselations = await modelPart.getAllTessellations();

// Чтение тесселляций привело к выделению компонентом большого объема памяти. Освободим неиспользуемую память.
await bimDataProvider.flushMemory();

// Получаем последнюю версию свойств элемента модели
const properties = await modelPart.getElementProperties(elements[5].guid, BimDataBigIntMaxValue);

// Завершаем работу с файлом модели, освобождаем объект посредник.
await modelPart.close();
await modelPart.dispose();

// Получаем объект посредник для чтения .cloudbm файла
const cloudPart = await bimDataProvider.openCloudPart("uniqueCloudPartId", cloudbmFileBuffer);

// Получаем метаданные облака точек
const metadata = cloudPart.getCloudMetadata();

// Получаем данные о иерархии октодерева облака точек.
const hierarchy = cloudPart.getCloudHierarchy();

// Получаем список точек узла октодерева
const points = cloudPart.getCloudPoints(hierarchy[0].dataIndex);

// Завершаем работу с файлом облака точек, освобождаем объект посредник.
await cloudPart.close();
await cloudPart.dispose();

// Завершаем работу компонента, освобождаем выделенные ресурсы.
await bimDataProvider.dispose();
```