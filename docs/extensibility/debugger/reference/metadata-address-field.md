---
title: METADATA_ADDRESS_FIELD | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 505267eac618a65434457b0e77f5d53da8e00ee1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967478"
---
# <a name="metadataaddressfield"></a>METADATA_ADDRESS_FIELD
Diese Struktur stellt die Adresse eines Felds, einer Klasse oder Struktur dar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```csharp  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## <a name="terms"></a>Begriffe  
 tokField  
 Die ID der dem Feld-Token.  
  
 [C++] `_mdToken` ist eine `typedef` für eine 32-Bit- `int`.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist Teil der Union in der [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Kontostruktur, wenn die `dwKind` Feld der `DEBUG_ADDRESS_UNION` Struktur nastaven NA hodnotu `ADDRESS_KIND_FIELD` (ein Wert aus der [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) die Enumeration).  
  
## <a name="requirements"></a>Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)