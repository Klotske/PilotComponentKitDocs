---
title: "ExtensionManager"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 9
---

**ExtensionManager** -- это класс-менеджер расширений, позволяет зарегистрировать или разрегистрировать расширения в компоненте **PilotWeb3D**. 

`ExtensionManager` доступен из пространства имен **PilotWeb3D** через свойство `theExtensionManager`.

Пример:

```js
// описываем расширение
class MyExtension extends PilotWeb3D.Extension {
  ...
}
// регистрируем
PilotWeb3D.theExtensionManager.registerExtensionType('myExtension', MyExtension);
```

## Методы

### registerExtensionType()

Метод регистрирует новое расширение в системе. После этого это расширение можно загрузить.
```js
registerExtensionType(extensionId: string, extension: typeof Extension) : boolean;
```
где:

`extensionId` -- уникальное имя расширения.

`extension` -- тип расширения унаследованный от `PilotWeb3d.Extension` или `PilotWeb2D.Extension`


### unregisterExtensionType()

Метод разрегистрирует расширение.
```js
unregisterExtensionType(extensionId: string) : boolean;
```
где:
`extensionId`-- идентификатор расширения.


### getExtensionType()

Метод получает тип зарегистрированного расширения.
```js
getExtensionType(extensionId: string): typeof Extension
```
где:
`extensionId`-- идентификатор расширения.
