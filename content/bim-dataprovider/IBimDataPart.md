---
title: IBimDataPart
draft: false
weight: 1
---


**IBimDataPart** -- базовый интерфейс объекта-посредника для чтения и записи файлов модели или облаков точек.

```js
export interface IBimDataPart {
  id: string;
  open(buffer: ArrayBuffer): Promise<void>;
  close(): Promise<void>;
  dispose(): Promise<void>;
}
```

## Поля

### id
Уникальный идентификатор файла модели.
```js
  id: string;
```

## Методы

### open()
Метод перезаписывает файл модели новыми данными.
```js
  open(buffer: ArrayBuffer): Promise<void>;
```
где:\
`buffer` -- массив данных файла модели.

### close()
Метод завершает работу с файлом модели и удаляет его из памяти.
```js
  close(): Promise<void>;
```

### dispose()
Метод завершает работу объекта-посредника и освобождает выделенные ресурсы. Файл модели также удаляется из памяти.
```js
  close(): Promise<void>;
```