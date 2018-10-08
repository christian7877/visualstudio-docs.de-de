---
title: IDebugOutputStringEvent2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cceb929a7f75420e1b93f15d653a48c1e112798e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522850"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugOutputStringEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugoutputstringevent2).  
  
Diese Schnittstelle wird von der Debug-Engine (DE) für die Sitzung Debug-Manager (SDM) Ausgabe eine Zeichenfolge gesendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um eine Zeichenfolge zum Senden der **Ausgabe** Fenster der IDE. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet dieses Ereignisobjekt, senden Sie eine Zeichenfolge, die die **Ausgabe** Fenster. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn es um das derzeit debuggte Programm angefügt wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode der `IDebugOutputStringEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Ruft die anzeigbare Meldung ab.|  
  
## <a name="remarks"></a>Hinweise  
 In nicht verwaltetem Code kann beispielsweise die Zeichenfolge, die Ausgabe stammen, wenn das derzeit debuggte Programm eine Zeichenfolge der Win32-sendet `OutputDebugString` Funktion. Diese Zeichenfolge wird durch die DE abgefangen und gesendet, das SDM als die `IDebugOutputStringEvent2` Ereignis.  
  
 Verwendung [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) zum Senden einer Nachricht, die eine Antwort des Benutzers erforderlich sind.  
  
 Verwendung [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) eine Fehlermeldung gesendet, die keine Antwort erforderlich ist.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
