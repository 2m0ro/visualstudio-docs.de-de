---
title: IDebugBreakpointRequest3::GetRequestInfo2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4290c34d37cfd5c444702d6040d7c934e698d53f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904863"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
Diese Methode ruft Informationen zu den Haltepunkt, der diese Anforderung Breakpoint beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```csharp  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFields`  
 [in] Eine Kombination von Flags aus der [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) Enumeration, die bestimmen, welche Felder der `pBPRequestInfo` in ausgefüllt werden.  
  
 `bBPRequestInfo`  
 [out] Die [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur gefüllt werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt den Fehlercode zurück.  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen in dieser Anforderung als von zurückgegeben wird das [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)