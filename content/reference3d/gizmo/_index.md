---
title: "Gizmo"
date: 2022-08-04T12:44:03+03:00
draft: false
weight: 3
---

## GizmoControl
[GizmoControl](./GizmoControl) -- контроллер, помещаемый на сцену, позволяющий изменять положение объектов на сцене.

## GizmoAxis
[GizmoAxis](./GizmoAxis) -- базовый класс осей `GizmoControl`.

[GizmoTranslationAxis](./GizmoTranslationAxis) -- встроенная реализация оси переноса.\
[GizmoRotationAxis](./GizmoRotationAxis) -- встроенная реализация оси вращения.\
[GizmoScaleAxis](./GizmoScaleAxis) -- встроенная реализация оси масштабирования.

## GizmoObject
[IGizmoObject](./IGizmoObject) -- базовый интерфейс гизмо объектов.\
[GizmoObject](./IGizmoObject#GizmoObject) -- встроенная реализация интерфейса `IGizmoObject`.

[GizmoMaterials](./GizmoMaterials) -- материалы, используемые объектами гизмо.

## GizmoBuilder
[GizmoBuilder](./GizmoBuilder) -- вспомогательный класс, для построения `GizmoControl`, с реализацией по умолчанию.