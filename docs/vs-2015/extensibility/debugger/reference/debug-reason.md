---
title: DEBUG_REASON | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b94b1503e5f12cbcb7aa120fd816302d9a305b5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844587"
---
# <a name="debugreason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt an, warum der Prozess zum Debuggen gestartet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parameter  
 DEBUG_REASON_ERROR  
 Ein nicht-spezifischer Fehler aufgetreten ist (Dies wird verwendet, als eine standardbedingung Wenn keine der anderen Lösung Gründe).  
  
 DEBUG_REASON_USER_LAUNCHED  
 Der Prozess wurde auf Anforderung des Benutzers gestartet.  
  
 DEBUG_REASON_USER_ATTACHED  
 Der bereits ausgeführten Prozess wurde vom Benutzer zugeordnet.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 Der Prozess wurde mit automatisch verbunden, wenn sie gestartet wurde.  
  
 DEBUG_REASON_CAUSALITY  
 Der Prozess wurde gestartet, aufgrund einer *Just-In-Time-* Debuggen (JIT)-Ereignis.  
  
## <a name="remarks"></a>Hinweise  
 Zurückgegeben von der [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)

