---
title: 'Idisperror:: GetSource | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetSource
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07c87585a92415f0b910210a56efa47e6f91417b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573086"
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Gibt den sprach abhängigen programmatischen Bezeichner für die Klasse oder die Anwendung zurück, die den Fehler ausgelöst hat.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstrSource`  
 vorgenommen Eine Zeichenfolge, die einen programmgesteuerten Bezeichner im Formular `progname.objectname` enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, um die Klasse oder die Anwendung zu bestimmen, in der die Ausnahme aufgetreten ist. Der programmgesteuerte Bezeichner kann in der Sprache zurückgegeben werden, die durch den Gebiets Schema Bezeichner (Locale Identifier, LCID) angegeben wird, der zum Zeitpunkt des auf  
  
> [!NOTE]
> Diese Methode ist nicht implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispError-Schnittstelle](../../winscript/reference/idisperror-interface.md)