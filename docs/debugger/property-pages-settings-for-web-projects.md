---
title: Eigenschafteneinstellungen für Webprojekte | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a9ab4300484e81e70abd36dbdba28521f91cd62
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903940"
---
# <a name="property-pages-settings-for-web-projects"></a>Einstellungen von Eigenschaftenseiten für Webprojekte
Sie können die Eigenschafteneinstellungen für eine Website-Debugkonfiguration im Dialogfeld **Eigenschaftenseiten** ändern. Eine genaue Anweisung finden Sie unter [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Dialogfeld **Eigenschaftenseiten** zu finden sind.

### <a name="start-options-category"></a>Starten Sie die Kategorie mit Optionen

| **Einstellung** | **Beschreibung** |
| - | - |
| **Startaktion** | Überschrift, unter der sich Optionen für den Anwendungsstart befinden. |
| **Aktuelle Seite verwenden** | Legt die aktuelle Seite als Ausgangspunkt für das Debuggen fest. |
| **Bestimmte Seite:** | Gibt die Webseite an, bei der das Debuggen beginnen soll. |
| **Externes Programm starten:** | Gibt den Startbefehl für das Programm an, das gedebuggt werden soll. |
| **Befehlszeilenargumente:** | Gibt Argumente für den oben aufgeführten Befehl an. |
| **Arbeitsverzeichnis:** | Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ist das Verzeichnis, über das die Anwendung gestartet wird: standardmäßig \bin\debug. |
| **Start-URL** | Gibt den Pfad der Webanwendung an, die gedebuggt werden soll. |
| **Keine Seite öffnen, sondern auf eine Anforderung einer externen Anwendung warten** | Legt fest, dass auf die Anforderung einer externen Anwendung gewartet wird. Mit dieser Option wird weder Internet Explorer noch eine andere Anwendung gestartet. Sie wird lediglich zum Debuggen vorbereitet, wenn sie von einer Anwendung aufgerufen wird. |
| **Server** | Überschrift, unter der sich Optionen zum zu verwendenden Server befinden. |
| **Standardwebserver verwenden** | Legt fest, dass der Standardwebserver verwendet wird. |
| **Benutzerdefinierten Server verwenden** | Ermöglicht es Ihnen, die Basis-URL einzugeben, die als Server verwendet werden soll. |
| **Debugger** | Überschrift, unter der sich Optionen zum Debugtyp befinden. |
| **ASP.NET-Debuggen** | Ermöglicht das Debuggen von Serverseiten, die für die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Entwicklungsplattform geschrieben wurden. Sie müssen unter **Start-URL** eine URL angeben. |
| **Debuggen von nativem Code** | Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen. |
| **SQL Server debuggen** | Ermöglicht das Debuggen von SQL Server-Datenbankobjekten. |
| **Silverlight-Debuggen** | Ermöglicht das Debuggen von Silverlight-Komponenten. |

## <a name="see-also"></a>Siehe auch
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)