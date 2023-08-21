---
title: "SettingsBase"
date: 2023-08-14T12:52:00+03:00
draft: false
---

**SettingsBase** -- класс, управляющий настройками вьювера (сохранение, получение). SettingsBase реализует интерфейс ISettings. Настройки сохраняются локально в localStorage с указанным префиксом. Префикс назначается путём реализации метода getKeyWithPrefix в классах наследниках.

```js
export abstract class SettingsBase implements ISettings
```

**ISettings** - интерфейс управления настройками через вьювер, использует ISettingsStorage. Подробнее: [ISettingsStorage](../SettingsLocalStorage)

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

### getKeyWithPrefix()
Метод возвращает ключ настройки с префиксом. Реализуется наследниками SettingsBase.
```js
abstract getKeyWithPrefix(key: string): string;
```
где:

`key` -- ключ без префикса для получения настройки.