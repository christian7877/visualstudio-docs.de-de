---
title: IDebugBeforeSymbolSearchEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugBeforeSymbolSearchEvent2 interface
ms.assetid: 679fd7b1-765a-41a8-a046-63240c09a499
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83e71b6059f19840311075261940942010f2e99e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349555"
---
# <a name="idebugbeforesymbolsearchevent2"></a>IDebugBeforeSymbolSearchEvent2
Die Debug-Engine (DE) sendet diese Schnittstelle für die Sitzung Debug-Manager (SDM), um den Status festzulegen Leiste Nachricht während des Symbols lädt.

## <a name="syntax"></a>Syntax

```
IDebugBeforeSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle auf, wenn diese Meldung in der Statuszeile bei Lasten des Symbols festgelegt werden muss. Diese Schnittstelle wird nur von Debug-Engines implementiert, die mit Geschäfts-, Schul- oder sind ein Teil der Skript-Interpreter. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden (wird verwendet, das SDM **QueryInterface** für den Zugriff auf die **IDebugEvent2** Schnittstelle).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, wenn diese Meldung in der Statuszeile bei Lasten des Symbols festgelegt werden muss. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM angegeben wird, wenn diese an die zu debuggende Programm wird angefügt.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt die Methoden der `IDebugBeforeSymbolSearchEvent2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetModuleName](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2-getmodulename.md)|Ruft den Namen des Moduls, die gerade gedebuggt werden.|

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll