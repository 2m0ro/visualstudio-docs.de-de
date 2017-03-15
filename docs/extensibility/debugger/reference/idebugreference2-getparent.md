---
title: "IDebugReference2::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetParent"
helpviewer_keywords: 
  - "IDebugReference2::GetParent"
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetParent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den übergeordneten Verweis eines Verweises ab.  Für zukünftige Verwendung reserviert.  
  
## Syntax  
  
```cpp#  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### Parameter  
 `ppParent`  
 \[out\]  Gibt ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Objekt zurück, das das übergeordnete Element dieser Eigenschaft darstellt.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)