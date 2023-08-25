---
title: "ExtensionManager"
date: 2022-08-29T14:44:03+03:00
draft: false
weight: 9
---

**ExtensionManager** -- это класс-менеджер расширений, позволяет зарегистрировать или разрегистрировать расширения в компоненте **PilotWeb2D**. 

`ExtensionManager` доступен из пространства имен **PilotWeb2D** через свойство `theExtensionManager`.

Пример:

```js
// описываем расширение
class MyExtension extends PilotWeb2D.Extension {
  ...
}
// регистрируем
PilotWeb2D.theExtensionManager.registerExtensionType('myExtension', MyExtension);
```

## Методы

### registerExtensionType()

Метод регистрирует новое расширение в системе. После этого это расширение можно загрузить.
```js
registerExtensionType(extensionId: string, extension: typeof Extension) : boolean;
```
где:\

`extensionId` -- уникальное имя расширения.

`extension` -- тип расширения унаследованный от `PilotWeb2D.Extension`


### unregisterExtensionType()

Метод разрегистрирует расширение.
```js
unregisterExtensionType(extensionId: string) : boolean;
```
где:\
`extensionId`-- уникальное имя расширения.


### getExtensionType()

Метод получает тип зарегистрированного расширения.
```js
getExtensionType(extensionId: string): typeof Extension
```
где:\
`extensionId`-- уникальное имя расширения.
