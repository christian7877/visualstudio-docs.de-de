---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20a8180283e596eeb9dd4ee1391e6e8fe6666829
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310172"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Diese Methode erstellt einen schnellansichtsdienst.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parameter
`binder`\
[in] Die [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt übergeben, um [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
[in] Die [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt übergeben, um `IDebugParsedExpression::EvaluateSync`.

`pAddress`\
[in] Die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt übergeben, um `IDebugParsedExression::EvaluateSync`.

`dataProvider`\
[in] Ein Objekt, das die [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Schnittstelle (bereitgestellt von der ausdrucksauswertung).

`ppService`\
[out] Der erstellte Dienst.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die `binder`, `pSymProv`, und `pAddress` Parameter wurden zum Übergeben der `IDebugParsedExpression::EvaluateSync` Methode. `CreateVisualizerService` nur aus aufgerufen werden soll `IDebugParsedExpression::EvaluateSync` als Teil einer ausdrucksauswertung-Unterstützung für Typ-Schnellansichten.

## <a name="see-also"></a>Siehe auch
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)