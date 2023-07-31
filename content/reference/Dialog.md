---
title: "Dialog"
date: 2023-07-03T12:59:03+03:00
draft: false
---

**Dialog** -- класс для создания диалоговых окон

## ElementClass {#ElementClass}
**ElementClass** -- интерфейс, добавляющий названия классов к заголовку, контенту и панели к которой прикреплен диалог. 

```js
export interface ElementClass {
  //Свойство, которое устанавливает класс панели к которой прикреплен диалог.
  panelClassName?: string;
  //Свойство, которое устанавливает класс контента диалога.
  contentClassName?: string;
  //Свойство, которое устанавливает класс заголовока диалога.
  headerClassName?: string;
}
```

## Конструктор
```js
  constructor(id: string, panelToAttach: HTMLElement);
```
где:\
`id`-- идентификатор диалога.\
`panelToAttach` -- элемент на странице к которому будет прикреплено диалоговое окно.

## Свойства

### dialog  {#dialog}
Получает созданный элемент диалога.
```js
get dialog(): HTMLElement;
```

### dialogContent  {#dialogContent}
Получает созданный элемент контента внутри диалога.
```js
get dialogContent(): HTMLElement;
```

### resizable  {#resizable}
Получает флаг, который показывает возможность изменения размеров окна.
```js
get resizable(): boolean;
```

## Методы

### setDialogContent()
Устанавливает содержимое диалога и возвращает класс Dialog.
```js
setDialogContent(value: HTMLElement): Dialog
```
где:\
`value` - HTML представление элемента.

### setHeader()
Устанавливает заголовок диалога и возвращает класс Dialog.
```js
setHeader(value: HTMLElement): Dialog
```
где:\
`value` - HTML представление элемента.

### setFooter()
Устанавливает нижний колонтитул диалога и возвращает класс Dialog.
```js
setFooter(value: HTMLElement): Dialog
```
где:\
`value` - HTML представление элемента.

### setDialogElementClassNames()
Устанавливает css классы содержимого в диалоговом окне и возвращает класс Dialog.
```js
setDialogElementClassNames(value: ElementClass): Dialog
```
где:\
`value` - объект с названиями классов для элементов внутри диалога.

### setResizable()
Устанавливает возможность изменения ширины и высоты диалога, возвращает класс Dialog.
```js
setResizable(value: boolean): Dialog
```
где:\
`value` - флаг для назначения включения и выключения возможности изменения размеров окна.

### setWindowOptions()
Устанавливает настройки для измнения положения и ширины/высоты диалога, возвращает класс Dialog. Без этой опции диалог не будет сохранять свои изменённые свойства. Подробнее: [IWindowStateOptions](../WindowStater#IWindowStateOptions).
```js
setWindowOptions(value: IWindowStateOptions): Dialog
```
где:\
`value` - настройки для работы измнения положения и ширины/высоты диалога.

### setDraggable()
Устанавливает возможность изменения положения диалога, возвращает класс Dialog.
```js
setDraggable(value: boolean): Dialog
```
где:\
`value` - флаг для назначения включения/выключения возможности изменения положения.


### openDialog()
Создаёт компонет диалога на panelToAttach и возвращает его как HTMLElement.
```js
openDialog(): HTMLElement
```

### destroyDialog()
Уничтожает компонет диалога.
```js
destroyDialog(): void
```

### isDialogShown()
Возвращает состояние диалога, закрыт/открыт.
```js
isDialogShown(): boolean
```

### subscribe()
Подписка на состояние диалога, закрыт/открыт.
```js
subscribe(fn: (state: boolean) => void): void
```
где:\
`fn` - функция callback для обработки события открытия/закрытия окна.
`state` - состояние открыт или закрыт диалог.