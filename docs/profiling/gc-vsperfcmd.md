---
title: GC (VSPerfCmd) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50b2e269ec292aaf37b8d0c707fa27ff8268a1f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969707"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
Die Option **GC** aktiviert das Erfassen von Daten zur Speicherbelegung durch .NET-Framework und zur Objektlebensdauer. Die Option **GC** kann nur gemeinsam mit der Sampling-Profilerstellungsmethode und der Option **Launch** (Start) verwendet werden.

 Wenn Sie die Option **GC** verwenden, ist der VSPerfClrEnv-Befehl **/sampleon** nicht erforderlich.

 Wenn keine Parameter angegeben sind, oder wenn der Parameter **Speicherbelegung** angegeben ist, werden nur Daten zur Speicherbelegung durch .NET-Framework erfasst. Wenn der Parameter **Lebensdauer** angegeben ist, werden sowohl Daten zur Speicherbelegung durch .NET-Framework als auch zur Objektlebensdauer erfasst.

## <a name="syntax"></a>Syntax

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parameter
 **Allocation** (Standard): Erfasst Daten zur Speicherbelegung durch .NET-Framework.

 **Lifetime**: erfasst sowohl Daten zur Speicherbelegung durch .NET-Framework als auch zur Lebensdauer von .NET Framework-Objekten.

## <a name="required-options"></a>Erforderliche Optionen
 Die Option **GC** kann nur mit der Option **Launch** (Start) verwendet werden.

 **Launch:** `AppName` startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.

## <a name="example"></a>Beispiel
 Mithilfe des folgenden Beispiels wird eine Anwendung gestartet und Daten zur Speicherbelegung durch .NET-Framework erfasst.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Siehe auch
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profilerstellung für Dienste](../profiling/command-line-profiling-of-services.md)