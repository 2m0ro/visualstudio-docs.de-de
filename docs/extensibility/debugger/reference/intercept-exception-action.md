---
title: "INTERCEPT_EXCEPTION_ACTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "INTERCEPT_EXCEPTION_ACTION"
helpviewer_keywords: 
  - "INTERCEPT_EXCEPTION_ACTION-enumeration"
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche Aktionen durchgeführt werden sollen, wenn Ausnahmen abgefangen werden.  
  
## Syntax  
  
```cpp#  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```c#  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### Parameter  
 IEA\_INTERCEPT  
 Aktiviert die aktuelle Ausnahme abfangend.  Dies ist der einzige Wert, der die aktuelle Uhrzeit basiert und muss angegeben werden.  
  
## Hinweise  
 Diese Werte werden in die [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)\-Methode übergeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)