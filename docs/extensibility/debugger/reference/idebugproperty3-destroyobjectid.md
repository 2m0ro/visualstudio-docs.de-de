---
title: IDebugProperty3::DestroyObjectID | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 540427286306999b25fba99a2efbd17013740d90
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869742"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Zerstört die eindeutige ID dieser Eigenschaft zugeordnet, der angibt, dass der Aufrufer nicht mehr wichtig, um diese Eigenschaft über alle anderen Eigenschaften eindeutig zu identifizieren.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn die Debug-Engine nicht eindeutige IDs für eine Eigenschaft zu unterstützen (da es bereits diese eindeutig intern nachverfolgt), wird einfach zurückgegeben kann `E_NOTIMPL` für diese Methode.

 Eindeutige IDs werden erstellt, durch einen Aufruf der [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) Methode, wenn der Aufrufer sicherstellen, dass diese Eigenschaft für alle anderen Eigenschaften eindeutig identifiziert wird.

## <a name="see-also"></a>Siehe auch
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)