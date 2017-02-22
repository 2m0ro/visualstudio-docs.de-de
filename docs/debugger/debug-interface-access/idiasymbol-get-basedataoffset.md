---
title: "IDiaSymbol::get_baseDataOffset | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: bb2ff5ed-9293-4c37-9741-654058b571c5
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_baseDataOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft den Datenoffset ab.  
  
## Syntax  
  
```cpp  
HRESULT get_baseDataOffset(   
   DWORD* pRetVal);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\] Ein Zeiger auf `DWORD`, der den grundlegenden Datenoffset enthält.  
  
## Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)