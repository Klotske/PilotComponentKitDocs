---
title: "ExtensionLoader"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 9
---

`ExtensionLoader` -- класс, отвечающий за загрузку и инициализацию зарегистрированных (в компоненте) расширений.


## Методы

### loadExtension()

Метод загружает и инициализирует зарегистрированное расширение.

```js
loadExtension(extensionId: string): Promise<Extension>;
```
где:
`extensionId` -- уникальное имя расширения.

### unloadExtension()

Метод выгружает расширение.

```js
unloadExtension(extensionId: string) : Promise<boolean>;
```
где:
`extensionId` -- уникальное имя расширения.

### getExtensions()

Метод получает все загруженные расширения.

```js
getExtensions(): Extension[] ;
```