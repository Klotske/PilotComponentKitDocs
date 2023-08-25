---
title: "ISettings"
date: 2023-08-14T12:52:00+03:00
draft: false
---

**ISettings** - интерфейс управления настройками через вьювер.
```js
export interface ISettings {
  changeSetting<T>(name: string, value: T, notify?: boolean, providedData?: any): void;
  getSettingValue<T>(name: string): T;
}
```

## Методы

### changeSetting()
Метод изменяющий настройку вьювера
```js
changeSetting<T>(name: string, value: T, notify?: boolean, providedData?: any): void;
```
где:

`name` -- имя настройки.\
`value` -- значение настройки.\
`notify` -- флаг для работы _eventDispatcher, если ничего не передано или true, то выбросит событие для подписчиков.\
`providedData` -- дополнительные данные, если необходимо получить подписчикам _eventDispatcher.

### getSettingValue()
Метод возвращает настройку вьювера
```js
getSettingValue<T>(name: string): T;
```
где:

`name` -- имя настройки.