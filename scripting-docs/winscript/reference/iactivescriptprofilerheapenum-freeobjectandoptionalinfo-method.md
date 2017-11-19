---
title: 'Iactivescriptprofilerheapenum:: Freeobjectandoptionalinfo-Methode | Microsoft Docs'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fdd5f7cc-be4e-4c13-a181-6320d26b44eb
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 748e5dbc948cc22e084a4e0b1e13222174bb739e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptprofilerheapenumfreeobjectandoptionalinfo-method"></a>IActiveScriptProfilerHeapEnum::FreeObjectAndOptionalInfo-Methode
Gibt den angegebenen [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md) Strukturen und ihre zugeordneten [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) Elemente.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT FreeObjectAndOptionalInfo (    [in] ULONG celt,    [in, size_is(celt)] PROFILER_HEAP_OBJECT** heapObjects);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 Die Anzahl der Objekte freizugeben.  
  
 `heapObjects`  
 Ein Array von [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md) Strukturen.  
  
## <a name="return-value"></a>Rückgabewert  
 Das HRESULT.