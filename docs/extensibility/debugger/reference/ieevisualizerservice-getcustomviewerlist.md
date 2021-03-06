---
title: IEEVisualizerService::GetCustomViewerList | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4fa71a731843f1deed1cfe9a464cc4ab716a8a43
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350170"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Diese Methode gibt eine Liste der Typ-Schnellansichten, denen diesen Dienst bekannt sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celtSkip`\
[in] Die Anzahl von Schnellansichten, zu überspringen.

`celRequested`\
[in] Anzahl von Schnellansichten abrufen (gibt auch die Größe der an die `rgViewers` Array).

`rgViewers`\
[in, out] Array von [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen gefüllt werden soll.

`pceltFetched`\
[out] Die Anzahl von Schnellansichten, die tatsächlich abgerufen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) übergibt die Anforderung an diese Methode als Teil der Unterstützung für Typ-Schnellansichten. Wenn die ausdrucksauswertung auch benutzerdefinierten Viewer für den gleichen Typ bereitstellt, können sie entsprechend ausgefüllte Anfügen [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen für diesen benutzerdefinierten Viewer zur Liste. Stellen Sie sicher, dass [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) diese zusätzliche Viewer widerspiegelt.

 Finden Sie unter [Typschnellansicht und benutzerdefinierte Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Weitere Informationen zu den Unterschieden zwischen Schnellansichten und -Viewer.

## <a name="see-also"></a>Siehe auch
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)