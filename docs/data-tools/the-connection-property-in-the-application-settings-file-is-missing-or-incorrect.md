---
title: Die Verbindungseigenschaft in der Application Settings-Datei fehlt oder ist fehlerhaft.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 77724510-ff59-4d43-b933-a0434e1ac597
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: d125c5e12320f0c2a17e12c53ca62764f4dfe79f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070815"
---
# <a name="the-connection-property-in-the-application-settings-file-is-missing-or-incorrect"></a>Die Verbindungseigenschaft in der Application Settings-Datei fehlt oder ist fehlerhaft.

Die Verbindungseigenschaft fehlt in der Datei mit den Anwendungseinstellungen, oder sie ist falsch. Stattdessen wurde die Verbindungszeichenfolge aus der *DBML*-Datei verwendet.

Die *DBML*-Datei enthält einen Verweis auf eine Verbindungszeichenfolge in der Datei mit den Anwendungseinstellungen, die nicht gefunden wurde. Diese Meldung dient zu Informationszwecken. Die Einstellung für die Verbindungszeichenfolge wird erstellt, wenn auf **OK** geklickt wird.

Wählen Sie auf diese Meldung reagieren, **OK**. Die Verbindungsinformationen, die in der *DBML*-Datei enthalten sind, werden den Anwendungseinstellungen hinzugefügt.

## <a name="see-also"></a>Siehe auch

- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)