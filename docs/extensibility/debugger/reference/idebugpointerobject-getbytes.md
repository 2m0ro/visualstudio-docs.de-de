---
title: IDebugPointerObject::GetBytes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a2c93e032175ce556d5504ed8b3f57dcf619a61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842703"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Ruft den Wert als eine Reihe von aufeinander folgenden Bytes gezeigt wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

#### <a name="parameters"></a>Parameter
 `dwStart`

 [in] Ein Offset in Bytes vom Beginn des Objekts auf den verwiesen wird.

 `dwCount`

 [in] Die Anzahl der abzurufenden Bytes.

 `pBytes`

 [in, out] Ein Array, das mit dem Wert als eine Reihe von aufeinander folgenden Bytes gefüllt ist, auf die am angegebenen Offset aus dem Objekt ab.

 `pdwBytes`

 [out] Gibt die Anzahl der Bytes, die tatsächlich abgerufen.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird verwendet, wenn der Zeiger, dargestellt durch diese [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) verweist auf einen primitiven Typ oder einem einfachen Array primitiver Typen (d. h. ein Array, das durch eine einfache Folge von Bytes dargestellt werden können).

## <a name="see-also"></a>Siehe auch
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)