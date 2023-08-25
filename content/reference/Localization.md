---
title: "Localization"
date: 2023-06-29T14:44:03+03:00
draft: false
---

**Localization** -- это класс для управления локализацией компонентов. Компоненты **PilotWeb3D** и **PilotWeb2D** используют библиотеку <a href="https://www.i18next.com">i18next</a> для поддержки локализации. На данный момент поддерживаются 2 языка: `ru` и `en`.

## Методы

### initialize()
Инициализировать локализацию компонента.
```js
static initialize(options: any): Promise<void>
```
где:\
 `options`: - опции для указания какой язык использовать. 

Пример:
```js
  const options = {
    language: "ru"
  }
```

### translate()
Получить переведенный текст на заданном языке.
```js
static translate(stringToTrans: string): string;
```
где:\
 `stringToTrans`: - ключ указанный в `translation.json`. Подробнее: <a href="https://www.i18next.com">i18next documentation</a>.


### setLanguage()
Изменить текущий язык для компонентов.

```js
static setLanguage(language: string): Promise<void>;
```
где:\
 `language`: - новый язык. Например: `ru` или `en`.


### extendLocalization()
Добавить дополнительную локализацию.

```js
static extendLocalization(locales: any): boolean;
```
где:\
 `locales`: - дополнительная локализация для модуля расширения.


Пример использования:

Файл `/assets/locales/en/translation.json`
```json
{
  "Extension": {
    "title": "Properties"
  }
}
```
Файл `ExtensionLocales.js`
```js
import json_en from '/assets/locales/en/translation.json';
import json_ru from '/assets/locales/ru/translation.json';

export const locales = {
  en: json_en,
  ru: json_ru
};
```

Файл `Extension.js`
```js
import { locales } from './ExtensionLocales';
export class Extension extends PilotWeb3D.Extension {

  constructor(viewer: PilotWeb3D.Viewer3D, options?: object) {
    super(viewer, options);

    // Добавляем локализацию для нашего расширения
    PilotWeb3D.Localization.extendLocalization(locales);

    // ... 

    // Получить локализованную строку
    const title = PilotWeb3D.Localization.translate('Extension.title');
  }
}

```