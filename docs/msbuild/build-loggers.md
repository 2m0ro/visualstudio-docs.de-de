---
title: Buildprotokollierungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c5bb6bbd3d05c22b7615a027ac3fcf6aa686156
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823027"
---
# <a name="build-loggers"></a>Buildprotokollierungen
Protokollierungen bieten eine Möglichkeit, die Ausgabe des Builds anzupassen und Meldungen, Fehler oder Warnungen als Reaktion auf bestimmte Buildereignisse anzuzeigen. Jede Protokollierung wird als .NET- Klasse implementiert, die die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle implementiert, die in der Assembly *Microsoft.Build.Framework.dll* definiert ist.

Es gibt zwei Ansätze, die Sie verwenden können, wenn Sie eine Protokollierung implementieren:

- Implementieren Sie die <xref:Microsoft.Build.Framework.ILogger>-Schnittstelle direkt.
- Leiten Sie Ihre Klasse von der Hilfsklasse <xref:Microsoft.Build.Utilities.Logger> ab, die in der Assembly *Microsoft.Build.Utilities.dll* definiert ist. <xref:Microsoft.Build.Utilities.Logger> implementiert <xref:Microsoft.Build.Framework.ILogger> und bietet standardmäßig Implementierungen einiger <xref:Microsoft.Build.Framework.ILogger>-Elemente.

  In diesem Thema wird erläutert, wie Sie eine einfache Protokollierung schreiben, die von <xref:Microsoft.Build.Utilities.Logger> abgeleitet ist und Meldungen in der Konsole als Reaktion auf bestimmte Buildereignisse anzeigt.

## <a name="register-for-events"></a>Registrieren für Ereignisse
Der Zweck einer Protokollierung ist das Sammeln von Informationen über den Fortschritt des Builds gemäß Meldung durch die Build-Engine und Berichten dieser Informationen auf nützliche Weise. Alle Protokollierungen müssen die <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>-Methode überschreiben, wo sich die Protokollierung für Ereignisse registriert. In diesem Beispiel registriert sich die Protokollierung für die <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>-, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>- und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>-Ereignisse.

[!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]

## <a name="respond-to-events"></a>Reagieren auf Ereignisse
Weil die Protokollierung nun für bestimmte Ereignisse registriert ist, muss sie diese Ereignisse bei ihrem Auftreten behandeln. Für die <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>- und <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>-Ereignisse schreibt die Protokollierung einfach einen kurzen Ausdruck und den Namen der am Ereignis beteiligten Projektdatei. Alle Meldungen aus der Protokollierung werden im Konsolenfenster ausgegeben.

[!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]

## <a name="respond-to-logger-verbosity-values"></a>Reagieren auf Ausführlichkeitswerte der Protokollierung
In einigen Fällen möchten Sie möglicherweise nur Informationen von einem Ereignis protokollieren, wenn der Schalter **-verbosity** von „MSBuild.exe“ einen bestimmten Wert enthält. In diesem Beispiel protokolliert der <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>-Ereignishandler nur dann eine Meldung, wenn die <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A>-Eigenschaft, die durch den Schalter **-verbosity** festgelegt wird, gleich <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed` ist.

[!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]

## <a name="specify-a-logger"></a>Festlegen einer Protokollierung
Nachdem die Protokollierung in eine Assembly kompiliert worden ist, müssen Sie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] mitteilen, diese Protokollierung während der Builderstellung zu verwenden. Dies erfolgt mithilfe des Schalters **-logger** von *MSBuild.exe*. Weitere Informationen zu den verfügbaren Schaltern für *MSBuild.exe* finden Sie in der [MSBuild-Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md).

Die folgende Befehlszeile erstellt das Projekt *MyProject.csproj* und verwendet die in *SimpleLogger.dll* implementierte Protokollierungsklasse. Der Schalter **-nologo** blendet Banner und Copyrightmeldung aus, und **-noconsolelogger** deaktiviert die standardmäßige [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Konsolenprotokollierung.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll
```

Die folgende Befehlszeile erstellt das Projekt mit der gleichen Protokollierung, jedoch mit dem `Verbosity`-Grad `Detailed`.

```cmd
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed
```

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung
Das folgende Beispiel enthält den vollständigen Code für die Protokollierung.

### <a name="code"></a>Code
[!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung
Das folgende Beispiel zeigt das Implementieren einer Protokollierung, die das Protokoll in eine Datei schreibt, anstatt es im Konsolenfenster anzuzeigen.

### <a name="code"></a>Code
[!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]

## <a name="see-also"></a>Siehe auch
- [Erhalten von Buildprotokollen](../msbuild/obtaining-build-logs-with-msbuild.md)
- [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
