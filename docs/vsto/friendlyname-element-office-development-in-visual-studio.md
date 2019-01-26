---
title: '&lt;FriendlyName&gt; -Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d038e825173f95ddfe4106022c7c9924090b3a5f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873105"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;FriendlyName&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `friendlyName` -Element des `vstov4` Namespace speichert den angezeigten Namen in der Liste der installierten Programme.

## <a name="syntax"></a>Syntax

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `friendlyName` -Element befindet sich im `vstov4` Namespace. Der Wert wird in der Liste der installierten Programme auf dem Computer und im Dialogfeld der COM-VSTO-Add-Ins von Microsoft Office-Anwendungen angezeigt.

 Das `friendlyName` Element weist keine Attribute oder untergeordnete Elemente auf.

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht das `friendlyName` -Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellten Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)