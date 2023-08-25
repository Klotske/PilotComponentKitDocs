---
title: "ExtensionLoader"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 9
---

`ExtensionLoader` -- это класс, предназначенный для загрузки и инициализации расширений, которые были зарегистрированы в компонентах. 
Перед тем, как загрузить расширение, его необходимо зарегистрировать с помощью `ExtensionManager`.

Пример:

```js
// описываем расширение
class MyExtension extends PilotWeb2D.Extension {
  ...
}
// регистрируем
PilotWeb2D.theExtensionManager.registerExtensionType('myExtension', MyExtension);

// загружаем в компонент
let viewer = PilotWeb2D.CreateViewer(div);
viewer.extensionLoader.loadExtension('myExtension');
```

## Методы

### loadExtension()

Метод загружает зарегистрированное расширение в компонент.

```js
loadExtension(extensionId: string): Promise<Extension>;
```
где:\
`extensionId` -- уникальное имя расширения.

### unloadExtension()

Метод выгружает расширение.

```js
unloadExtension(extensionId: string) : Promise<boolean>;
```
где:\
`extensionId` -- уникальное имя расширения.

### getExtensions()

Метод получает все загруженные расширения.

```js
getExtensions(): Extension[] ;
```