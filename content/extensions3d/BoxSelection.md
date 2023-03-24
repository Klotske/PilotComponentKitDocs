---
title: "BoxSelectionExtension"
date: 2023-01-01T14:44:03+03:00
draft: false
---

**BoxSelectionExtension** -- расширение, которое позволяет селектировать элементы с помощью рамки.\
Для того чтобы выделить объекты рамкой: зажмите и удерживайте клавишу `Shift`, затем зажмите и удерживайте левую кнопку мыши - появится рамка выделения. После появления рамки можно больше не зажимать клавишу `Shift`.

Выделение рамкой слева-направо выделяет только полностью содержащиеся внутри рамки объекты.\
Рамка рисуется голубым цветом.

Выделение рамкой справа-налево выделяет все объекты касающиеся рамки.\
Рамка рисуется зелёным цветом.

Расширение имеет имя `PilotWeb3D.BoxSelection`.

Пример подключения в `html`:
```html
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/BoxSelection3D/BoxSelection.min.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.BoxSelection");
```

## Методы

### activate()
Активировать расширение. Расширение подписывается на события клавиатуры и мыши.
```js
activate(): void;
```
### deactivate()
Деактивировать расширение. Расширение отписывается от событий клавиатуры и мыши.
```js
deactivate(): void;
```