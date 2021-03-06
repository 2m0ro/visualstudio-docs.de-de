---
title: Visualisieren und Anzeigen von Daten | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 852616ac77096a5b31078d64051f67f6cbb3ecb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912828"
---
# <a name="visualizing-and-viewing-data"></a>Visualisieren und Anzeigen von Daten
Typschnellansichten und benutzerdefinierten Viewern Darstellung der Daten in einer Weise, die schnell für Entwickler relevant ist. Die ausdrucksauswertung (EE) kann Drittanbieter-Typ-Schnellansichten unterstützen als auch einen eigenen benutzerdefinierten Viewer angeben.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Bestimmt, wie viele typschnellansichten und benutzerdefinierten Viewern den Typ des Objekts zugeordnet, durch den Aufruf sind der [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) Methode. Wenn Sie mindestens einen typschnellansicht oder in benutzerdefinierten Viewer verfügbar ist, ruft Visual Studio die [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methode zum Abrufen einer Liste dieser Schnellansichten und-Viewer (eigentlich eine Liste von s, die die Schnellansichten implementiert und -Viewer) und präsentiert diese dem Benutzer.

## <a name="supporting-type-visualizers"></a>Typ-Schnellansichten unterstützen
 Es gibt eine Reihe von Schnittstellen, die die EE implementieren müssen, um Typ-Schnellansichten unterstützen. Diese Schnittstellen können in zwei große Kategorien untergliedert werden: Schnittstellen, die die Typ-Schnellansichten und Schnittstellen, die Zugriff auf die Eigenschaftendaten aufgeführt.

### <a name="listing-type-visualizers"></a>Typ-Schnellansichten auflisten
 Die EE unterstützt Auflisten der Typ-Schnellansichten in seiner Implementierung von `IDebugProperty3::GetCustomViewerCount` und `IDebugProperty3::GetCustomViewerList`. Diese Methoden übergeben, den Aufruf an die entsprechenden Methoden [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md).

 Die [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) durch Aufruf von [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Diese Methode erfordert die [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) -Schnittstelle, die aus abgerufen werden die [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Schnittstelle zu übergeben, um [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). `IEEVisualizerServiceProvider::CreateVisualizerService` erfordert außerdem die [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) und [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) Schnittstellen, die übergeben wurden `IDebugParsedExpression::EvaluateSync`. Die endgültige Benutzeroberfläche, die zum Erstellen der `IEEVisualizerService` Schnittstelle ist die [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) -Schnittstelle, die die EE implementiert. Diese Schnittstelle ermöglicht Änderungen an die Eigenschaft, die Schnellansicht angezeigt wird. Alle Daten in gekapselt ein [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) -Schnittstelle, die auch von der EE implementiert wird.

### <a name="accessing-property-data"></a>Zugreifen auf Daten
 Zugreifen auf die Daten erfolgt über die [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstelle. Um diese Schnittstelle abzurufen, ruft Visual Studio [QueryInterface](/cpp/atl/queryinterface) auf der, der abzurufende Eigenschaftenobjekt die [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle (auf das gleiche Objekt, das implementiert implementiert die [ IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle) und ruft dann die [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) Methode zum Abrufen der `IPropertyProxyEESide` Schnittstelle.

 Alle Daten zu übergeben, in und aus der `IPropertyProxyEESide` Schnittstelle gekapselt ist, der [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle. Diese Schnittstelle stellt ein Array von Bytes und wird von Visual Studio und die EE implementiert. Wenn Daten für eine Eigenschaft geändert werden, erstellt Visual Studio ein `IEEDataStorage` Objekt, das die neuen Daten und ruft [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) mit diesem Datenobjekt, um ein neues erhalten `IEEDataStorage` Objekt, das wiederum die an [InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md) zum Aktualisieren von Daten von der Eigenschaft. `IPropertyProxyEESide::CreateReplacementObject` ermöglicht die EE, eine eigene Klasse zu instanziieren, die implementiert die `IEEDataStorage` Schnittstelle.

## <a name="supporting-custom-viewers"></a>Unterstützung von benutzerdefinierten Viewern
 Das Flag `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` festgelegt ist, der `dwAttrib` Feld der [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) Struktur (zurückgegeben durch einen Aufruf von [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) um anzugeben, dass das Objekt einen benutzerdefinierten Viewer verknüpft ist mit ihm. Wenn dieses Flag festgelegt ist, ruft Visual Studio die [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle aus der [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle. dabei wird [QueryInterface](/cpp/atl/queryinterface).

 Wenn der Benutzer einen benutzerdefinierten Viewer auswählt, wird Visual Studio instanziiert den benutzerdefinierten Viewer, die mithilfe des anzeigenden Benutzers `CLSID` vom die `IDebugProperty3::GetCustomViewerList` Methode. Visual Studio ruft dann [DisplayValue](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) auf den Wert für dem Benutzer anzuzeigen.

 In der Regel `IDebugCustomViewer::DisplayValue` stellt eine schreibgeschützte Ansicht der Daten. Um Änderungen an den Daten zu ermöglichen, muss die EE eine benutzerdefinierte Schnittstelle implementieren, die sich verändernden Daten auf ein Objekt unterstützt werden. Die `IDebugCustomViewer::DisplayValue` Methode, die diese benutzerdefinierte Schnittstelle verwendet, um das Ändern von Daten unterstützt. Die Methode sucht die benutzerdefinierte Schnittstelle, auf die `IDebugProperty2` Schnittstelle als übergeben, die `pDebugProperty` Argument.

## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>Unterstützung von sowohl typschnellansichten und benutzerdefinierten Viewern
 Ein EE unterstützen sowohl typschnellansichten und benutzerdefinierten Viewern in die [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) und [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) Methoden. Zuerst fügt die EE die Anzahl der benutzerdefinierten Viewer, die er bereitstellt, die den Rückgabewert von der [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) Methode. Zweitens: die EE fügt die `CLSID`s der Liste zurückgegeben werden, indem Sie einen eigenen benutzerdefinierten Viewer die [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) Methode.

## <a name="see-also"></a>Siehe auch
- [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)
- [Typschnellansicht und benutzerdefinierter viewer](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)