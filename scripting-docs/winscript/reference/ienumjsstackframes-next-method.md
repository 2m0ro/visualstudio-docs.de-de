---
title: 'Ienumjsstackframes:: Next-Methode | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1838d6494311502faf99d86c80e0a74ded4c6e5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092403"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next-Methode
Ruft die angegebene Anzahl an Frames ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `cFrameCount`  
 [in] Die Anzahl der abzurufenden Frames.  
  
 `pFrames`  
 [out] Das Array, um die Frames zu speichern.  
  
 `pcFetched`  
 [out] Die Anzahl der zurückgegebenen Frames.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumJsStackFrames-Schnittstelle](../../winscript/reference/ienumjsstackframes-interface.md)