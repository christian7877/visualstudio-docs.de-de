---
title: IDebugPendingBreakpoint2::CanBind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::CanBind
helpviewer_keywords:
- IDebugPendingBreakpoint2::CanBind method
- CanBind method
ms.assetid: 84a2b189-ccf1-467e-8fab-0c0da68f0b91
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9325d8a0c8ee39aec6f8ceccb5bbb894eef2163
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311732"
---
# <a name="idebugpendingbreakpoint2canbind"></a>IDebugPendingBreakpoint2::CanBind
Bestimmt, ob diese ausstehende Haltepunkt an einen Speicherort gebunden werden kann.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanBind ( 
   IEnumDebugErrorBreakpoints2** ppErrorEnum
);
```

```csharp
int CanBind ( 
   out IEnumDebugErrorBreakpoints2 ppErrorEnum
);
```

## <a name="parameters"></a>Parameter
`ppErrorEnum`\
[out] Gibt eine [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) -Objekt, das eine Liste der enthält [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) Objekte an, wenn es möglicherweise Fehler.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK.` gibt `S_FALSE` Wenn der Haltepunkt nicht gebunden werden kann, in diesem Fall die Fehler werden zurückgegeben von der `ppErrorEnum` Parameter. Andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Haltepunkt gelöscht wurde.

## <a name="remarks"></a>Hinweise
 Diese Methode wird aufgerufen, um zu bestimmen, was passieren würde, wenn diese ausstehenden Haltepunkt gebunden wurde. Rufen Sie die [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) Methode, um den ausstehenden Haltepunkt tatsächlich zu binden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CPendingBreakpoint` -Objekt, das macht die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Schnittstelle.

```cpp
HRESULT CPendingBreakpoint::CanBind(IEnumDebugErrorBreakpoints2** ppErrorEnum)
{
   HRESULT hr;
   HRESULT hrT;

   // Check for a valid pointer to an error breakpoint enumerator
   // interface; otherwise, return hr = E_INVALIDARG.
   if (ppErrorEnum)
   {
      // Verify that the pending breakpoint has not been deleted. If
      // deleted, then return hr = E_BP_DELETED.
      if (m_state.state != PBPS_DELETED)
      {
         // Verify that the breakpoint is a file/line breakpoint.
         if (IsFlagSet(m_pBPRequest->m_bpRequestInfo.dwFields, BPREQI_BPLOCATION) &&
             m_pBPRequest->m_bpRequestInfo.bpLocation.bpLocationType == BPLT_CODE_FILE_LINE)
         {
            hr = S_OK;
         }
         // If the breakpoint type is not a file/line breakpoint, then the
         // result should be an error breakpoint.
         else
         {
            // If the error breakpoint member variable does not have
            // allocated memory.
            if (!m_pErrorBP)
            {
               // Create, AddRef, and initialize a CErrorBreakpoint object.
               if (CComObject<CErrorBreakpoint>::CreateInstance(&m_pErrorBP) == S_OK)
               {
                  m_pErrorBP->AddRef();
                  m_pErrorBP->Initialize(this);
               }
            }

            // Create a new enumerator of error breakpoints.
             CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;
            if (CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum) == S_OK)
            {
               // Get the IDebugErrorBreakpoint2 information for the
               // CErrorBreakpoint object.
               CComPtr<IDebugErrorBreakpoint2> spErrorBP;
               hrT = m_pErrorBP->QueryInterface(&spErrorBP);
               assert(hrT == S_OK);
               if (hrT == S_OK)
               {
                  // Initialize the new enumerator of error breakpoints
                  // with the IDebugErrorBreakpoint2 information.
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };
                  hrT = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);
                  if (hrT == S_OK)
                  {
                     // Verify that the passed IEnumDebugErrorBreakpoints2
                     // interface can be successful queried by the
                     // created CEnumDebugErrorBreakpoints object.
                     hrT = pErrorEnum->QueryInterface(ppErrorEnum);
                     assert(hrT == S_OK);
                  }
               }

               // Otherwise, delete the CEnumDebugErrorBreakpoints object.
               if (FAILED(hrT))
               {
                  delete pErrorEnum;
               }
            }

            hr = S_FALSE;
         }
      }
      else
      {
         hr = E_BP_DELETED;
      }
   }
   else
   {
      hr = E_INVALIDARG;
   }

   return hr;
}
```

## <a name="see-also"></a>Siehe auch
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)