---
title: "SettingsBase"
date: 2023-08-14T12:52:00+03:00
draft: false
---

**SettingsBase** -- класс, предоставляющий функционал работы с настройками. Настройки сохраняются локально.

**ISettings** - интерфейс управления настройками во вьюверах.

```js
export interface IEventsDispatcher {
  changeSetting<T>(name: string, value: T, notify?: boolean, providedData?: any): void;
  getSettingValue<T>(name: string): T;
}
```

## Методы

### changeSetting()
Изменить настройку вьювера
```js
changeSetting<T>(name: string, value: T, notify?: boolean, providedData?: any): void;
```
где:

`name` -- имя настройки.\
`value` -- значение настройки.\
`notify` -- флаг для работы _eventDispatcher, если ничего не передано или true, то выбросит событие для подписчиков.\
`providedData` -- дополнительные данные, если необходимо получить подписчикам _eventDispatcher.

### getSettingValue()
Получить настройку вьювера
```js
getSettingValue<T>(name: string): T;
```
где:

`name` -- имя настройки.

### getKeyWithPrefix()
Получить настройку вьювера с необходимым префиксом. Реализуется наследниками SettingsBase.
```js
abstract getKeyWithPrefix(key: string): string;
```
где:

`key` -- ключ без префикса для получения настройки.