---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugManagedObject::SetFromManagedObject
helpviewer_keywords: IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3f73236b45edea7a9dea003a1f3604669eb3739
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Legt den Wert der Instanz des Klassenobjekts Wert aus der Instanz der Wertklasse als Parameter bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pManagedObject`  
 [in] Eine Schnittstelle, die das verwaltete Objekt mit dem neuen Wert darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird verwendet, um das verwaltete Objekt zu ändern, dargestellt durch die [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) Objekt.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)