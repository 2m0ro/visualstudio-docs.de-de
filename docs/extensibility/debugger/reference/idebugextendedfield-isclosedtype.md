---
title: IDebugExtendedField::IsClosedType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9056a3543de27b26bc32eec5840248c337ea11fa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678331"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Bestimmt, ob das Feld einen geschlossenen Typ darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsClosedType(
   void
);
```

```csharp
int IsClosedType();
```

## <a name="return-value"></a>Rückgabewert
 Wenn das Feld einen geschlossenen Typ ist, gibt `S_OK`ist, andernfalls gibt `S_FALSE`.

## <a name="see-also"></a>Siehe auch
- [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)