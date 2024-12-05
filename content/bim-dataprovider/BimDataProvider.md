---
title: "BimDataProvider"
draft: false

---
**BimDataProvider** -- основной класс компонента.

Компонент работает с файлами данных модели и облаков точек.\
Используемая файловая система определяется окружением компонента: в Node.js окружении, либо в небезопасном контексте браузерного окружения будет использоваться MEMFS - файловая система, работающая с файлами только в оперативной памяти.\
В [безопасном контексте](https://developer.mozilla.org/en-US/docs/Web/Security/Secure_Contexts) браузерного окружения будет использоваться [OPFS](https://developer.mozilla.org/en-US/docs/Web/API/File_System_API/Origin_private_file_system) - файловая система, позволяющая работать с файлами на диске.

```js
type FSType = 'OPFS' | 'MEMFS';

class BimDataProvider {
  get usedFSType(): FSType;

  init(): Promise<void>;
  createDataFile(id: string): Promise<IBimDataPart>;
  openModelPart(dataFile: IBimDataPart): Promise<IBimDataModelPart | undefined>;
  openModelPart(id: string, buffer: ArrayBuffer): Promise<IBimDataModelPart | undefined>;
  openCloudPart(dataFile: IBimDataPart): Promise<IBimDataCloudPart | undefined>;
  openCloudPart(id: string, buffer: ArrayBuffer): Promise<IBimDataCloudPart | undefined>;
  dispose(): Promise<void>;
  flushMemory(): Promise<void>;
}
```

## Свойства

### usedFSType
Свойство определяет тип используемой файловой системы.
```js
  get usedFSType(): FSType;
```
где `FSType` - тип файловой системы: `MEMFS` или `OPFS`.


## Методы

### init()
Метод инициализирует компонент.
```js
  init(): Promise<void>;
```

### createDataFile()
Метод создает файл в файловой системе для чтения и записи.
```js
  createDataFile(id: string): Promise<IBimDataPart | undefined>;
```
где:\
`id` -- уникальный идентификатор файла модели.\
Возвращает объект-посредник для чтения и записи файла данных. Подробнее: [IBimDataPart](../IBimDataPart).

### openModelPart()
Метод открывает файл модели для чтения и записи.
```js
  openModelPart(dataFile: IBimDataPart): Promise<IBimDataModelPart | undefined>;
  openModelPart(id: string, buffer: ArrayBuffer): Promise<IBimDataModelPart | undefined>;
```
где:\
`dataFile` -- объект посредник для чтения или записи файла данных. Подробнее: [IBimDataPart](../IBimDataPart).\
или:\
`id` -- уникальный идентификатор файла модели.\
`buffer` -- массив данных файла модели.\
Возвращает объект-посредник для чтения или записи файла модели, если удалось открыть файл. Подробнее: [IBimDataModelPart](../IBimDataModelPart).
В противном случае возвращает `undefined`.

### openCloudPart()
Метод открывает файл облака точек для чтения.
```js
  openCloudPart(dataFile: IBimDataPart): Promise<IBimDataModelPart | undefined>;
  openCloudPart(id: string, buffer: ArrayBuffer): Promise<IBimDataCloudPart | undefined>;
```
где:\
`dataFile` -- объект посредник для чтения или записи файла облака точек. Подробнее: [IBimDataPart](../IBimDataPart).\
или:\
`id` -- уникальный идентификатор файла облака точек.\
`buffer` -- массив данных файла облака точек.\
Возвращает объект-посредник для чтения файла облака точек, если удалось открыть файл. Подробнее: [IBimDataCloudPart](../IBimDataCloudPart).
В противном случае возвращает `undefined`.

### dispose()
Метод завершает работу компонента и освобождает выделенные ресурсы.
```js
  dispose(): Promise<void>;
```
{{< hint type="important" title="Важно">}}
После завершения работы компонента чтение файлов модели и облаков точек через объекты-посредники невозможно.
{{< /hint >}}

### flushMemory()
Метод освобождает память, выделенную компонентом, без завершения работы компонента.
```js
  flushMemory(): Promise<void>;
```
{{< hint type="important" title="Важно">}}
Метод не должен вызываться одновременно с чтением или записью файлов модели или облаков точек через объекты-посредники.
{{< /hint >}}


## Пример использования
```js
import { BimDataBigIntMaxValue, BimDataProvider } from "@pilotdev/pilot-bim-dataprovider";

// --- Работа с файлами частей модели ---
// Создаем и инициализируем компонент.
const bimDataProvider = new BimDataProvider();
await bimDataProvider.init();

// Получаем объект-посредник для чтения .bm файла.
const modelPart = await bimDataProvider.openModelPart("uniqueModelPartId", bmFileBuffer);

// Получаем список всех элементов части модели.
const elements = await modelPart.getAllElements();

// Получаем список всех тесселяций объектов модели.
const tesselations = await modelPart.getAllTessellations();

// Чтение тесселяций привело к выделению компонентом большого объема памяти. Освободим неиспользуемую память.
await bimDataProvider.flushMemory();

// Получаем последнюю версию свойств элемента модели.
const properties = await modelPart.getElementProperties(elements[5].guid, BimDataBigIntMaxValue);

// Завершаем работу с файлом модели, освобождаем объект-посредник.
await modelPart.close();
await modelPart.dispose();


// --- Работа с файлами облаков точек ---
// Получаем объект-посредник для чтения .cloudbm файла.
const cloudPart = await bimDataProvider.openCloudPart("uniqueCloudPartId", cloudbmFileBuffer);

// Получаем метаданные облака точек.
const metadata = cloudPart.getCloudMetadata();

// Получаем данные об иерархии октодерева облака точек.
const hierarchy = cloudPart.getCloudHierarchy();

// Получаем список точек узла октодерева.
const points = cloudPart.getCloudPoints(hierarchy[0].dataIndex);

// Завершаем работу с файлом облака точек, освобождаем объект-посредник.
await cloudPart.close();
await cloudPart.dispose();


// --- Работа с частичной записью файлов---
// Создаем объект-посредник для записи файла
const dataPart = await bimDataProvider.createDataFile("uniqueDataPartId");
// Пишем в файл по частям, где chunk0, chunk1, chunk2 - массивы данных в бинарном виде
await dataPart.write(chunk0, 0);  // пишем в начало файла
await dataPart.write(chunk1, chunk0.byteLength);  // продолжаем запись с того места где остановились
await dataPart.write(chunk2, chunk0.byteLength + chunk1.byteLength); // продолжаем запись с того места где остановились

const modelPart2 = await bimDataProvider.openModelPart(dataPart); // открываем файл как файл части модели

// Завершаем работу с файлом модели, освобождаем объект-посредник.
// Достаточно закрыть и освободить только modelPart2, dataPart закрывать и освобождать необязательно, так как он ссылается на тот же файл
await modelPart2.close();
await modelPart2.dispose();


// Завершаем работу компонента, освобождаем выделенные ресурсы.
await bimDataProvider.dispose();
```