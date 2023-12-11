---
title: "GizmoControl"
date: 2022-08-04T12:44:03+03:00
draft: false

---

[GizmoControl](./GizmoControl) -- контроллер, прикрепляемый к 3D-объекту на сцене и управляющий его положением.

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
[GizmoBuilder](./GizmoBuilder) -- вспомогательный класс для построения `GizmoControl` с реализацией по умолчанию.