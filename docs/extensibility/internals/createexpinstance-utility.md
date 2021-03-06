﻿---
title: CreateExpInstance-Hilfsprogramm | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c4f77d0eba4ca974522534c69d554af9d807a9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861918"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance-Hilfsprogramm
Verwenden der **CreateExpInstance** Hilfsprogramm zu erstellen, zurücksetzen oder löschen eine experimentelle Instanz von Visual Studio. Sie können die experimentelle Instanz zum Debuggen und Testen Visual Studio-Erweiterungen, ohne die zugrunde liegenden Produkt verwenden.

## <a name="syntax"></a>Syntax

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parameter
 **/ Erstellen Sie** die experimentelle Instanz erstellt.

 **/ Reset** löscht die experimentelle Instanz, und klicken Sie dann eine neue erstellt.

 **/ Clean** löscht die experimentelle Instanz.

 **/ VSInstance** den Namen des Verzeichnisses, das die zu kopierende grundlegende Visual Studio-Instanz enthält.

 **/ RootSuffix** das Suffix, auf den Namen des Verzeichnisses experimentelle Instanz angefügt werden soll.

## <a name="remarks"></a>Hinweise
 Wenn Sie Visual Studio-Erweiterung arbeiten, können Sie durch Drücken auf F5, um die standardmäßige experimentelle Instanz öffnen, und installieren Sie die aktuelle Erweiterung. Wenn keine experimentelle Instanz verfügbar ist, erstellt Visual Studio mit einem Konto mit den Standardeinstellungen.

 Der Standardspeicherort der experimentellen Instanz hängt von der Visual Studio-Versionsnummer ab. Für Visual Studio 2015, z. B. der Speicherort ist *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Alle Dateien in das Verzeichnis werden als Teil dieser Instanz betrachtet. Alle zusätzlichen experimentellen Instanzen werden nicht von Visual Studio geladen werden, es sei denn, der den Namen des Verzeichnisses am Standardspeicherort geändert wird.

 Visual Studio greift die Registrierung des Systems nicht, wenn sie die experimentelle Instanz geöffnet wird. Dies unterscheidet sich von früheren Versionen von Visual Studio, die eine experimentelle Version der Registrierungsstruktur verwendet.

 Die **CreateExpInstance** Hilfsprogramm ersetzt die **VsRegEx** Hilfsprogramm.

 Im folgenden Beispiel wird die Standardwert für die experimentellen Instanz von Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /rootsuffix=Exp**

## <a name="see-also"></a>Siehe auch
- [VSPackages](../../extensibility/internals/vspackages.md)
