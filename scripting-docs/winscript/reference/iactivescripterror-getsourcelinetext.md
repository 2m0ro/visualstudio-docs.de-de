---
title: IActiveScriptError::GetSourceLineText | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourceLineText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourceLineText
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3186ec3edcdd0c66f06f7b769eff31e8b050c428
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091701"
---
# <a name="iactivescripterrorgetsourcelinetext"></a>IActiveScriptError::GetSourceLineText
Ruft ab, die Zeile in der Quelldatei, in denen ein Fehler aufgetreten ist, während eine Skript-Engine ein Skript ausgeführt wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## <a name="parameter"></a>Parameter  
 `pbstrSourceLine`  
 [out] Die Adresse eines Puffers, der die Zeile des Quellcodes empfängt, in dem der Fehler aufgetreten ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_FAIL` , wenn die Zeile in der Quelldatei nicht abgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)