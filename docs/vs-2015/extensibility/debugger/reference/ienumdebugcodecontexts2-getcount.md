---
title: IEnumDebugCodeContexts2::GetCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::GetCount
helpviewer_keywords:
- IEnumDebugCodeContexts2::GetCount
ms.assetid: 74c52fcf-688c-40df-9acd-29b3b84e6216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e32a0d47fc1f07c3858b056d4483c762853bb428
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62551756"
---
# <a name="ienumdebugcodecontexts2getcount"></a>IEnumDebugCodeContexts2::GetCount
Gibt die Anzahl der Elemente in der Enumeration zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

#### <a name="parameters"></a>Parameter
 `pcelt`

 [out] Gibt die Anzahl der Elemente in der Enumeration zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode ist nicht Teil die übliche com-Enumerationsschnittstelle, der angibt, dass nur die `Next`, `Clone`, `Skip`, und `Reset` Methoden implementiert werden müssen.

## <a name="see-also"></a>Siehe auch
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)