---
title: "IDebugPortSupplierDescription2::GetDescription | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierDescription2::GetDescription"
ms.assetid: bff5f536-1cd1-4313-8856-db7b05818305
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplierDescription2::GetDescription
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Beschreibung und die Eigenschaftenmetadaten für den Anschlusslieferanten ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDescription(  
   PORT_SUPPLIER_DESCRIPTION_FLAGS *pdwFlags,  
   BSTR *pbstrText  
);  
```  
  
```c#  
public int GetDescription(  
   out enum_PORT_SUPPLIER_DESCRIPTION_FLAGS pdwFlags,  
   out string pbstrText  
);  
```  
  
#### Parameter  
 `pdwFlags`  
 \[out\]  Flags für Metadaten zur Beschreibung.  
  
 `pbstrText`  
 \[out\]  Beschreibung des Anschlusslieferanten.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)