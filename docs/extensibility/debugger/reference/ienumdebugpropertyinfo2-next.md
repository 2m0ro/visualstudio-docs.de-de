---
title: "IEnumDebugPropertyInfo2::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2::Next"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Next"
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPropertyInfo2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die nächste Gruppe von Elementen aus der Enumeration zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   DEBUG_PROPERTY_INFO** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                  celt,  
   DEBUG_PROPERTY_INFO[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der abzurufenden Elemente.  Gibt die maximale Größe des `rgelt` Arrays an.  
  
 `rgelt`  
 \[in, out\]  Array von Elementen, [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) ausgefüllt werden soll.  
  
 `pceltFetched`  
 \[out\]  Gibt die Anzahl der Elemente zurück, die sich tatsächlich in `rgelt`zurückgegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn kleiner als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)