---
title: IDiaPropertyStorage::ReadLONG | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7d9f9e6b91492651e82368a0b10148cbb4e069b5
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31460019"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Liest `LONG` Werte in einem Eigenschaftensatz.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `id`  
 [in] Bezeichner für die Eigenschaft gelesen werden (`PROPID` ist definiert in WTypes.h als eine `ULONG`).  
  
 `pValue`  
 [out] Gibt den Wert der Eigenschaft zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` Wenn die Eigenschaft nicht vom Typ `LONG`.  
  
## <a name="remarks"></a>Hinweise  
 Ein `LONG` von Windows als 32-Bit-Ganzzahl definiert ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)