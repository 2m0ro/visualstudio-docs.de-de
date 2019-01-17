---
title: IActiveScriptProfilerCallback::Shutdown | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.Shutdown
apilocation:
- scrobj.dll
ms.assetid: 1281bf3c-d7d8-4ff5-9d8a-d1761fdb262e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbe5acd75ecf4f004d835490579b1f35c1bf675c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346292"
---
# <a name="iactivescriptprofilercallbackshutdown"></a>IActiveScriptProfilerCallback::Shutdown
Wird aufgerufen, um das Profilerobjekt zu informieren, wenn auf eine Skript-Engine die profilerstellung beendet wird. Auf diese Weise kann das Profilerobjekt seine Bereinigungsroutinen aufrufen, wenn erforderlich. Diese Methode wird auch von der Skript-Engine aufgerufen, wenn die Skript-Engine heruntergefahren wird oder wenn ein Aufruf von [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) ein Fehler auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Shutdown(  
    [in] HRESULT hrReason);  
```  
  
#### <a name="parameters"></a>Parameter  
 `hrReason`  
 [in] Der Grund für das Herunterfahren. Wenn die Skript-Engine heruntergefahren wird, `S_OK` übergeben wird. Wenn der Aufruf von [IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md) einen HRESULT-Fehler zurückgibt, der HRESULT-Wert übergeben wird. Andernfalls wird dieser Wert abgerufen, von [IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Der Rückgabewert dieser Methode wird von der Skript-Engine ignoriert.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptProfilerCallback-Schnittstelle](../../winscript/reference/iactivescriptprofilercallback-interface.md)