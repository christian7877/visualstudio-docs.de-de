---
title: IDebugBinder::ResolveRuntimeType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2954b5f2a1ac4dd14485a1b924423ba53fddcb7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315164"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Diese Methode bestimmt der Laufzeittyp eines Objekts.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Parameter
`pObject`\
[in] Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) aufgelöst werden.

`ppResolved`\
[out] Gibt den Typ des Objekts als ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Laufzeittyp eines Objekts ist nicht immer zum Zeitpunkt der Kompilierung bekannt. Beispielsweise kann Polymorphismus verwendet wird, ein Argument an eine Funktion als Basisklasse, z. B. eine Button-Klasse übergeben werden. Das tatsächliche Argument möglicherweise eine abgeleitete Klasse wie z. B. eine Radio Button-Klasse.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)