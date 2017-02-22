---
title: "marker_series::write_message-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::write_message"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_message-Methode"
ms.assetid: 546121bc-67e0-4a5a-a456-12bd78fd6de2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::write_message-Methode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schreibt eine Meldung in die Parallelitätsschnellansichts\-Ablaufverfolgungsdatei.  
  
## Syntax  
  
```  
void write_message(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_message(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Parameter  
 `_Format`  
 Eine kombinierte Formatzeichenfolge, die Text vermischte mit null\) enthält oder mehr Formatelementen, die den Objekten in der Argumentliste entsprechen.  
  
 `_Importance`  
 Wichtigkeitsstufe.  
  
 `_Category`  
 Category.Importance\-Ebene.  
  
## Anforderungen  
 **Header:**  cvmarkersobj.h  
  
 **Namespace:**  Concurrency::diagnostic  
  
## Siehe auch  
 [marker\_series\-Klasse](../profiling/marker-series-class.md)