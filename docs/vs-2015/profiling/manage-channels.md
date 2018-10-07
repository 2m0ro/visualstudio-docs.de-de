---
title: Verwalten von Kanälen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.tools.managechannels
helpviewer_keywords:
- Concurrency Visualizer, Manage Channels
ms.assetid: 507b06e9-bb56-4a72-8fd5-f91f958da6fc
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48507f8133466c7ab48ba2992434c751a8e32014
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524752"
---
# <a name="manage-channels"></a>Verwalten von Kanälen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Kanäle verwalten](https://docs.microsoft.com/visualstudio/profiling/manage-channels).  
  
In der **Threadansicht** in der Parallelitätsschnellansicht können Sie die Kanäle für den Prozess so organisieren, dass Sie bestimmte Muster untersuchen können. Sie können Kanäle sortieren, sie nach oben und unten verschieben oder sie ausblenden und wieder einblenden.  
  
## <a name="sort-by"></a>Sortieren nach  
 Mit dem „Sortieren nach“-Steuerelement können Sie Threads nach verschiedenen Kriterien basierend auf dem aktuellen Zoomfaktor sortieren. Dies ist besonders nützlich, wenn Sie nach einem bestimmten Muster suchen. Sie können nach folgenden Kriterien sortieren:  
  
|Kriterien|Definition|  
|--------------|----------------|  
|Startzeit|Sortiert Threads nach ihren Startzeiten. Dies ist die standardmäßige Sortierreihenfolge.|  
|Endzeit|Sortiert Threads nach ihren Endzeiten.|  
|Ausführung|Sortiert Threads nach dem Prozentsatz der verstrichenen Zeit, die für die Ausführung benötigt wird.|  
|Synchronisierung|Sortiert Threads nach dem Prozentsatz der verstrichenen Zeit, die für die Synchronisierung benötigt wird.|  
|E/A|Sortiert Threads nach dem Prozentsatz der verstrichenen Zeit, die für die E/A (Lesen und Schreiben von Daten) benötigt wird.|  
|Sleep|Sortiert Threads nach dem Prozentsatz der verstrichenen Zeit, die für den Standbymodus benötigt wird.|  
|Paging|Sortiert Threads nach dem Prozentsatz der verstrichenen Zeit, die für das Paging benötigt wird.|  
|Vorzeitige Entfernung|Sortiert Threads nach dem Prozentsatz der verstrichenen Zeit, die für die vorzeitige Entfernung benötigt wird.|  
|Benutzeroberflächenverarbeitung|Sortiert Threads nach dem Prozentsatz der verstrichenen Zeit, die für die Benutzeroberflächenverarbeitung benötigt wird.|  
  
## <a name="move-selected-channel-up-or-down"></a>Ausgewählten Kanal nach oben oder unten verschieben  
 Diese Steuerelemente können Sie verwenden, um einen Kanal in der Liste nach oben oder unten zu verschieben. Beispielsweise können Sie verknüpfte Kanäle nebeneinander positionieren, damit Sie ein bestimmtes Muster oder eine threadübergreifende Beziehung untersuchen können.  
  
## <a name="move-selected-channel-to-top-or-bottom"></a>Ausgewählten Kanal nach oben oder unten verschieben  
 Sie können ausgewählte Kanäle nach oben oder unten in der Liste verschieben, damit Sie ein bestimmtes Muster untersuchen können, oder einige Kanäle aus dem Weg schieben, wenn Sie andere Kanäle überprüfen.  
  
## <a name="hide-selected-channels"></a>Ausblenden ausgewählter Kanäle  
 Wählen Sie dieses Steuerelement aus, wenn Sie Kanäle ausblenden möchten. Wenn ein Thread z.B. eine hundertprozentige Synchronisierung für die Dauer Ihres verwalteten Prozesses darstellt, können sie ihn verbergen, während Sie andere Threads analysieren.  
  
> [!NOTE]
>  Ein Thread wird auch durch Ausblenden aus der Berechnungszeit entfernt, die in der aktiven Legende und in den Profilberichten angezeigt wird.  
  
## <a name="show-all-channels"></a>Alle Kanäle anzeigen  
 Dieses Steuerelement ist aktiv, wenn ein Kanal oder mehrere Kanäle ausgeblendet sind. Wenn Sie dieses auswählen, werden alle ausgeblendeten Elemente angezeigt und werden an die Zeitberechnung zurückgegeben.  
  
## <a name="move-markers-to-top"></a>Marker nach oben verschieben  
 Wenn eine Ablaufverfolgung Markerereignisse enthält, können Sie diesen Befehl zum Verschieben der Markerkanäle in den oberen Bereich der Zeitachse verwenden. Die relative Reihenfolge wird beibehalten.  
  
## <a name="group-markers-by-thread"></a>Marker nach Threads gruppieren  
 Wenn die Ablaufverfolgung Markerereignisse enthält, können Sie diesen Befehl verwenden, um Markerkanäle unter dem Thread, der die Markerereignisse generiert hat, zu gruppieren.  Die Datenträgerkanäle werden an das obere Ende der Kanalliste verschoben, und GPU-Kanäle werden ganz nach unten verschoben.  
  
## <a name="see-also"></a>Siehe auch  
 [Zoomsteuerelement (Threadansicht)](../profiling/zoom-control-threads-view.md)   
 [Messmodus aktivieren/deaktivieren](../profiling/measure-mode-on-off.md)   
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)


