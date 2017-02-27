---
title: "IDebugProcess2::GetProcessId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::GetProcessId"
helpviewer_keywords: 
  - "IDebugProcess2::GetProcessId"
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::GetProcessId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die GUID für diesen Prozess ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetProcessId(  
   GUID* pguidProcessId  
);  
```  
  
```c#  
int GetProcessId(  
   out Guid pguidProcessId  
);  
```  
  
#### Parameter  
 `pguidProcessId`  
 \[out\]  Gibt die GUID für diesen Prozess zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der GUID \(Globally Unique Identifier\) gibt diesen Prozess von allen anderen Prozessen, die im System ausgeführt werden.  
  
## Siehe auch  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)