---
title: IDebugBoundBreakpoint2::GetPendingBreakpoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint method
- GetPendingBreakpoint method
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6827ea65deea153279c8d900dd759998758981e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856677"
---
# <a name="idebugboundbreakpoint2getpendingbreakpoint"></a>IDebugBoundBreakpoint2::GetPendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den ausstehenden Haltepunkt, der aus dem der angegebene gebundene Haltepunkt erstellt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBreakpoint  
);  
```  
  
```csharp  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppPendingBreakpoint`  
 [out] Gibt die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) -Objekt, das den ausstehenden Haltepunkt darstellt, der verwendet wurde, zum Erstellen dieser gebundene Haltepunkt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein ausstehender Haltepunkt kann betrachtet werden als Auflistung von alle erforderlichen Informationen erforderlich, um einen Haltepunkt in Code zu binden, die auf eine oder mehrere Programme angewendet werden können.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CBoundBreakpoint` -Objekt, das macht die [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Schnittstelle.  
  
```  
HRESULT CBoundBreakpoint::GetPendingBreakpoint(  
    IDebugPendingBreakpoint2** ppPendingBreakpoint)  
{    
   HRESULT hr;    
  
   // Check for valid IDebugPendingBreakpoint2 interface pointer.    
   if (ppPendingBreakpoint)    
   {    
      // Be sure that the bound breakpoint has not been deleted. If  
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugPendingBreakpoint2 interface.    
         hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,  
                                           (void**)ppPendingBreakpoint);    
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
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

