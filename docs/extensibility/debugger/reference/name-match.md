---
title: NAME_MATCH | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NAME_MATCH
helpviewer_keywords:
- NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50ae796a4662b51c186e6e9d69bf41771d040c8b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865689"
---
# <a name="namematch"></a>NAME_MATCH
Wählt den Fall kann Option für den Abgleich von Namen an.

## <a name="syntax"></a>Syntax

```cpp
typedef enum { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
} NAME_MATCH;
```

```csharp
public enum NameMatchOptions { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
}
```

## <a name="members"></a>Member
 NmNone, die keine Optionen angegeben sind.

 NmCaseSensitive gibt an, dass Namen abgeglichen wird Groß-/Kleinschreibung beachtet werden.

 NmCaseInsensitive gibt an, die zu entfernenden Namen sind nicht in der Groß-/Kleinschreibung beachtet.

## <a name="remarks"></a>Hinweise
 Übergeben als Argument für die folgenden Methoden:

- [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)

- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)

- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)

- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)
- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)