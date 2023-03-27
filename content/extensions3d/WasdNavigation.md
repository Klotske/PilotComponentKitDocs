---
title: "WasdNavigationExtension"
draft: false
---

**WasdNavigationExtension** -- расширение, которое позволяет навигироваться по сцене с помощью клавиатуры, либо с помощью методов API.\
Клавиши клавиатуры:
`W` - вперед,
`A` - влево,
`S` - назад,
`D` - вправо,
`Q` - вниз,
`E` - вверх,
`Shift` - ускорение.

Расширение имеет имя `PilotWeb3D.WasdNavigation`.

Пример подключения в `html`:
```html
...
<script src="https://pilotcloud.ascon.net/components/@VERSION@/extensions/WasdNavigation/WasdNavigation.min.js"></script>
...
```

Пример подключения в `javascript`:
```js
var htmlDiv = document.getElementById('pilotViewer')
viewer = PilotWeb3D.CreateViewer(htmlDiv);
viewer.start();
viewer.extensionsLoader.loadExtension("PilotWeb3D.WasdNavigation");
```

## Поля

### standardSpeed {#standardSpeed}
Скорость перемещения камеры по умолчанию.
```js
  standardSpeed: number = 5;
```

### increasedSpeed {#increasedSpeed}
Скорость перемещения камеры при ускоренном движении.
```js
  increasedSpeed: number = 30;
```

### timeAcceleratingToSpeedLimit
Время разгона камеры с [standardSpeed](#standardSpeed) до [increasedSpeed](#increasedSpeed).
```js
  timeAcceleratingToSpeedLimit: number = 500;
```

### speedGoingThroughObstacles {#speedGoingThroughObstacles}
Скорость перемещения камеры сквозь препятствия.
```js
  speedGoingThroughObstacles: number = 0.5;
```

### speedGoingThroughObstaclesIncreased {#speedGoingThroughObstaclesIncreased}
Скорость перемещения камеры сквозь препятствия при ускоренном движении.
```js
  speedGoingThroughObstaclesIncreased: number = 1;
```

### distanceToObstacleWhereStartToSlowDown {#distanceToObstacleWhereStartToSlowDown}
Расстояние до препятствия, начиная с которого камера начинает замедляться.
```js
  distanceToObstacleWhereStartToSlowDown: number = 500;
```

## Методы

### activate()
Включить подписку на события клавиатуры.
```js
activate(): void;
```

### deactivate()
Выключить подписку на события клавиатуры.
```js
deactivate(): void;
```

### setImpulseDirection()
Метод задаёт направление движения камеры.
```js
setImpulseDirection(dir: Direction, add: boolean): void;
```
где:
`dir` -- Направление движения отсносительно камеры. Подробнее: [Direction](#Direction).\
`add` -- `true` для добавления, `false` для вычитания.

### getImpulseDirection()
Метод возвращает направление движения камеры.
```js
getImpulseDirection(): Direction;
```
Возвращает перечисление [Direction](#Direction).

### setIncreasedImpulse()
Метод активирует ускоренное движение.
```js
setIncreasedImpulse(isIncreased: boolean): void;
```
где:\
`isIncreased` -- `true`, для ускоренного движения.

## Перечисление WasdNavigationExtension.Direction {#Direction}
Направления относительно камеры.
```js
export enum Direction {
  None = 0,
  Forward = 1 << 1,
  Left = 1 << 2,
  Backward = 1 << 3,
  Right = 1 << 4,
  Down = 1 << 5,
  Up = 1 << 6,
}
```