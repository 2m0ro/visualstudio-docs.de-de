---
title: IDebugErrorBreakpointResolution2::GetResolutionInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetResolutionInfo
ms.assetid: d94c4f60-8796-4848-86ee-186bbaa613f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f399c82e5bc5619e0690cb27245baab9944c9377
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874612"
---
# <a name="idebugerrorbreakpointresolution2getresolutioninfo"></a>IDebugErrorBreakpointResolution2::GetResolutionInfo
Ruft den Haltepunkt auflösen Fehlerinformationen ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetResolutionInfo( 
    BPERESI_FIELDS            dwFields,
    BP_ERROR_RESOLUTION_INFO* pErrorResolutionInfo
);
```

```csharp
int GetResolutionInfo( 
    enum_BPERESI_FIELDS        dwFields,
    BP_ERROR_RESOLUTION_INFO[] pErrorResolutionInfo
);
```

#### <a name="parameters"></a>Parameter
`dwFields`

[in] Eine Kombination von Flags aus der [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) Enumeration, die bestimmen, welche Felder der `pErrorResolutionInfo` ausgefüllt werden müssen.

`pErrorResolutionInfo`

[in, out] Die [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) -Struktur, die mit der Beschreibung der haltepunktauflösung gefüllt wird.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="example"></a>Beispiel
Das folgende Beispiel implementiert diese Methode für eine einfache `CDebugErrorBreakpointResolution` -Objekt, das macht die [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) Schnittstelle.

```cpp
HRESULT CDebugErrorBreakpointResolution::GetResolutionInfo(
    BPERESI_FIELDS dwFields,
    BP_ERROR_RESOLUTION_INFO* pBPErrorResolutionInfo)
{
    HRESULT hr;

    if (pBPErrorResolutionInfo)
    {
        // Copy the specified fields of the request information from the class member
        // variable to the local BP_ERROR_RESOLUTION_INFO variable.
        hr = CopyBP_ERROR_RESOLUTION_INFO(m_bpErrorResolutionInfo,
                                          *pBPErrorResolutionInfo,
                                          dwFields);
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}

HRESULT CDebugErrorBreakpointResolution::CopyBP_ERROR_RESOLUTION_INFO(
    BP_ERROR_RESOLUTION_INFO& bpResSrc,
    BP_ERROR_RESOLUTION_INFO& bpResDest,
    DWORD dwFields)
{
    HRESULT hr = S_OK;

    // Start with a raw copy.
    memcpy(&bpResDest, &bpResSrc, sizeof(BP_ERROR_RESOLUTION_INFO));

    // The fields in the destination is the result of the AND of bpInfoSrc.dwFields
    // and dwFields.
    bpResDest.dwFields = dwFields & bpResSrc.dwFields;

    // Fill in the bp location information if the BPERESI_BPRESLOCATION flag
    // is set in BPERESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_BPRESLOCATION))
    {
        // Switch on the BP_TYPE.
        switch (bpResSrc.bpResLocation.bpType)
        {
            case BPT_CODE:
            {
                // AddRef the IDebugCodeContext2 of the BP_RESOLUTION_CODE structure.
                bpResDest.bpResLocation.bpResLocation.bpresCode.pCodeContext->AddRef();
                break;
            }
            case BPT_DATA:
            {
                // Copy the bstrDataExpr, bstrFunc, and bstrImage of the
                // BP_RESOLUTION_DATA structure.
                bpResDest.bpResLocation.bpResLocation.bpresData.bstrDataExpr =
                SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrDataExpr);
                bpResDest.bpResLocation.bpResLocation.bpresData.bstrFunc =
                SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrFunc);
                bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage =
                SysAllocString(bpResSrc.bpResLocation.bpResLocation.bpresData.bstrImage);
                break;
            }
            default:
            {
                assert(FALSE);
                // Clear the BPERESI_BPRESLOCATION flag of the BPERESI_FIELDS
                // in the destination BP_ERROR_RESOLUTION_INFO.
                ClearFlag(bpResDest.dwFields, BPERESI_BPRESLOCATION);
                break;
            }
        }
    }
    // AddRef the IDebugProgram2 if the BPRESI_PROGRAM flag is set in the BPRESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_PROGRAM))
    {
        bpResDest.pProgram->AddRef();
    }
    // AddRef the IDebuThread2 if the BPRESI_THREAD flag is set in the BPRESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_THREAD))
    {
        bpResDest.pThread->AddRef();
    }
    // Check if the BPERESI_MESSAGE flag is set in the BPRESI_FIELDS.
    if (IsFlagSet(bpResDest.dwFields, BPERESI_MESSAGE))
    {
        // Copy the source bstrMessage into the destination bstrMessage.
        bpResDest.bstrMessage = SysAllocString(bpResSrc.bstrMessage);
        // Clear the destination flag if there is no message.
        if (!bpResDest.bstrMessage)
        {
            ClearFlag(bpResDest.dwFields, BPERESI_MESSAGE);
        }
    }

    return hr;
}
```

## <a name="see-also"></a>Siehe auch

- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
