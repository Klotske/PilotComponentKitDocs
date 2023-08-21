---
title: "SettingsLocalStorage"
date: 2023-08-14
draft: false
---

**ISettingsStorage** - интерфейс управления настройками в localStorage.

```js
export interface ISettingsStorage {
  clear(): void;
  getItem<T>(key: string): T | null;
  removeItem(key: string): void;
  setItem<T>(key: string, value: T): void;
  getKeys(): string[];
}
```

## Методы

### clear()
Удаляет все настройки
```js
clear(): void;
```

### getItem()
Метод возвращает значение настройки
```js
getItem<T>(key: string): T | null;
```
где:

`key` -- ключ сохранённой настройки.

### removeItem()
Метод удаляет значение настройки
```js
removeItem(key: string): void;
```
где:

`key` -- ключ для удаления настройки.

### setItem()
Метод устанавливает новое или перезаписывает существуещее значение
```js
setItem<T>(key: string, value: T): void;
```
где:

`key` -- ключ для установки настройки.
`value` -- значение настройки.

### getKeys()
Метода возвращает все ключи настроек
```js
getKeys(): string[];
```