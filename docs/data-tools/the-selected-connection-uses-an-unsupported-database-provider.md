---
title: Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e6ebdca67dd87f25111ba48c3d9baa346d00e4db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566136"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Die ausgewählte Verbindung nutzt einen nicht unterstützten Anbieter.

Diese Meldung wird angezeigt, wenn Sie Elemente ziehen, die nicht die .NET Framework-Datenanbieter für SQL Server verwenden **Server-Explorer** oder **Datenbank-Explorer** auf die [LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

Die **O/R Designer** unterstützt nur datenverbindungen, die den .NET Framework-Datenanbieter für SQL Server verwenden. Nur Verbindungen zu Microsoft SQL Server oder zur Microsoft SQL Server-Datenbankdatei sind gültig.

Um diesen Fehler zu beheben, fügen Sie nur Elemente von datenverbindungen, die .NET Framework-Datenanbieter für SQL Server verwenden, die **O/R Designer**.

## <a name="see-also"></a>Siehe auch

- <xref:System.Data.SqlClient>
- [O/R-Designer-Meldungen](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
