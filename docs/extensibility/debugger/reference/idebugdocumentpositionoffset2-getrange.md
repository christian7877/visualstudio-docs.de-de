---
title: IDebugDocumentPositionOffset2::GetRange | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c667ffa597481121de0467c9ab4b07e4bf4d607
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333386"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Ruft den Bereich für die aktuelle Dokumentposition ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRange(
   DWORD* pdwBegOffset,
   DWORD* pdwEndOffset
);
```

```csharp
public int GetRange(
   ref uint pdwBegOffset,
   ref uint pdwEndOffset
);
```

## <a name="parameters"></a>Parameter
`pdwBegOffset`\
[in, out] Offset für die Anfangsposition des Bereichs. Legen Sie diesen Parameter auf den Wert null, wenn diese Informationen nicht benötigt wird.

`pdwEndOffset`\
[in, out] Offset für die Endposition des Bereichs. Legen Sie diesen Parameter auf den Wert null, wenn diese Informationen nicht benötigt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In einen Dokumentposition für einen Positionshaltepunkt angegebene Bereich wird nun für eine Anweisung zu suchen, die tatsächlich beitragen von Code von der Debug-Engine (DE) verwendet. Beachten Sie z. B. folgenden Code:

```
Line 5: // comment
Line 6: x = 1;
```

 Zeile 5 unterstützt kein Code vorhanden, das derzeit debuggte Programm. Wenn der Debugger, der den Haltepunkt in Zeile 5 festlegt will die DE, um eine bestimmte Menge für die erste Zeile vorwärts zu suchen, die Code beteiligt sind, würde der Debugger einen Bereich angeben, der weitere Kandidat Zeilen enthält, wo ein Haltepunkt richtig platziert werden kann. Die DE würde dann vorwärts durch diese Zeilen suchen, bis er eine Zeile gefunden, die einen Haltepunkt akzeptieren konnte.

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)