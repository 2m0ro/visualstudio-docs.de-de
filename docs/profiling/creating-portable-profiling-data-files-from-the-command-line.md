---
title: Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b156de17c1f2ee43ccc215cf3723e14acd3c36b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405804"
---
# <a name="create-portable-profiling-data-files-from-the-command-line"></a>Erstellen portierbarer Profilerstellungsdatendateien über die Befehlszeile
Sie können das Befehlszeilentool [VSPerfReport](../profiling/vsperfreport.md) zum Einbetten der Symbole für eine Profilerstellungsausführung in die *VSP*-Datei verwenden, um die Freigabe der Profilerstellungsdaten zu vereinfachen.

 Sie können auch eine bereits analysierte Profilerstellungsdatendatei (*VSPS*) erstellen, die kleiner ist und schneller in der IDE geladen wird.

> [!NOTE]
> Stellen Sie sicher, dass die Symboldateien (*PDB*) von **VSPerfReport** verwendet werden können. Weitere Informationen finden Sie unter [Vorgehensweise: Angeben von Symboldateispeicherorten über die Befehlszeile](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).
>
> Weitere Informationen zur Pfadangabe für **VSReport** finden Sie unter [Angeben des Pfads zu den Profilerstellungstools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).
>
> Die Profilerstellungsdaten in einer *VSPS*-Datei können nicht gefiltert werden.

### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Einbetten von Symbolen in die Profilerstellungsdatendatei (*VSP*) für die Profilerstellungsausführung

- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   \<Pfad> <strong>VSPerfReport \<</strong>VSP-Datei> **/PackSymbols**

   Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.

### <a name="to-create-a-summary-profiling-data-file"></a>Erstellen einer zusammenfassenden Profilerstellungsdatendatei

- Geben Sie im Eingabeaufforderungsfenster folgenden Befehl ein:

   \<Pfad> <strong>VSPerfReport \<</strong>VSP-Datei> **/SummaryFile** [**/Output:**\<Dateiname>]

   Der Name der *VSPS*-Datei ist standardmäßig der Basisname der *VSP*-Datei. Sie können mit der Option **Output** allerdings einen alternativen Namen angeben.