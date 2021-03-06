---
title: IDebugMemoryBytes2::ReadAt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f787ad06b4e7d612007b6448287b5062ae1b0efd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873310"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Liest eine Folge von Bytes, beginnend ab einem bestimmten Standort.

## <a name="syntax"></a>Syntax

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

#### <a name="parameters"></a>Parameter
 `pStartContext`

 [in] Die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt, das angibt, wo Sie beginnen, Lesen von Bytes.

 `dwCount`

 [in] Die Anzahl der zu lesenden Bytes. Außerdem gibt die Länge des der `rgbMemory` Array.

 `rgbMemory`

 [in, out] Array mit den Bytes gefüllt, die tatsächlich gelesen werden.

 `pdwRead`

 [out] Gibt die Anzahl von zusammenhängenden Bytes, die tatsächlich gelesen.

 `pdwUnreadable`

 [in, out] Gibt die Anzahl der nicht gelesen Bytes zurück. Möglicherweise ein null-Wert ab, wenn der Client nicht die Anzahl der nicht lesbare Bytes ist.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn 100 Byte angefordert werden und die ersten 50 lesbar sind, die nächsten 20 nicht lesbar sind und die verbleibenden 30 lesbar sind, gibt diese Methode zurück:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 In diesem Fall da `*pdwRead + *pdwUnreadable < dwCount`, der Aufrufer muss einen zusätzlichen Aufruf der ursprünglichen Anforderung 100 verbleibenden 30 Bytes gelesen, und die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) Objekt übergeben, der `pStartContext` Parameter erweitert werden muss von 70.

## <a name="see-also"></a>Siehe auch
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)