---
title: Im Dialogfeld "Optionen" Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen,
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6506fec976822ea4a4e675c9961395c952a7a35f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970304"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Im Dialogfeld "Optionen" Microsoft Office Word-Tastatur, Microsoft Office-Tastatureinstellungen,
  Microsoft Office Word und Visual Studio behandelt sowohl Tastenkombinationen. Die gleichen Tastenkombination kann für verschiedene Befehle, die in Word und Visual Studio verwendet. Wenn Sie Word in einem Projekt auf Dokumentebene in Visual Studio geöffnet ist, empfängt jeweils nur eine Anwendung Befehle der Tastenkombination. Standardmäßig Visual Studio alle Befehle für Tastenkombination erhält, aber Sie können Word diese empfangen werden, wenn das Dokument den Fokus durch Auswahl besitzt **Dynamisches Tastaturschema**.

 Wenn Sie eine Tastenkombination, die nicht an einen Befehl in der Anwendung zugewiesen ist, die gerade die Tastenkombination gedrückt wird verwenden, wird die Tastenkombination für an eine andere Anwendung übergeben.

 Die von Ihnen auszuwählende Option bleibt für Word-Projekte wirksam, bis Sie ihn ändern. Die Auswahl wirkt sich nicht auf Microsoft Office Excel-Projekte aus; Sie müssen alle Änderungen für Excel, mit den Optionen für die Microsoft Office Excel-Tastatur.

## <a name="uielement-list"></a>UIElement-Liste
 **Visual Studio-Tastaturschema** Visual Studio erhält alle Tastenkombinationsbefehle, selbst wenn das Word-Dokument den Fokus besitzt. Wenn Sie die Taste z. B. **F5** während das Dokument den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.

 **Dynamisches Tastaturschema** Visual Studio erhält die Tastenkombinationsbefehle nur, wenn es den Fokus besitzt. Wenn Sie das Word-Dokument den Fokus besitzt, empfängt Word alle Kontextmenübefehle. Angenommen, Sie die Taste **F5** Word wird geöffnet, während das Word-Dokument den Fokus besitzt, die **suchen und Ersetzen** Dialogfeld mit der **Gehe zu** Registerkarte ausgewählt. Wenn Sie drücken **F5** während Visual Studio den Fokus besitzt, Visual Studio startet das Debuggen der Projektmappe.

## <a name="see-also"></a>Siehe auch
- [Im Dialogfeld "Optionen" Microsoft Office Excel-Tastatur, Microsoft Office-Tastatureinstellungen,](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
