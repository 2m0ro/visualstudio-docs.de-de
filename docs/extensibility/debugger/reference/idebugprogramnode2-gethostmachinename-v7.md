---
title: IDebugProgramNode2::GetHostMachineName_V7 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9ed7eb9c98ad8da45a50af79918480e74d76779e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908547"
---
# <a name="idebugprogramnode2gethostmachinenamev7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> ALS VERALTET MARKIERT. VERWENDEN SIE NICHT.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

#### <a name="parameters"></a>Parameter

`pbstrHostMachineName`  
[out] Gibt den Namen des Computers in der das Programm ausgeführt wird.

## <a name="return-value"></a>Rückgabewert

Eine Implementierung sollte immer zurückgeben `E_NOTIMPL`.

## <a name="remarks"></a>Hinweise

> [!WARNING]
> Ab Visual Studio 2005, diese Methode wird nicht mehr verwendet und sollte immer zurückgeben `E_NOTIMPL`.

## <a name="see-also"></a>Siehe auch

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)