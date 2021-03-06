---
title: Registerkarte ", Dialogfeld" Fenstereigenschaften "-Klasse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7f81a100b2c2311444732434df0f5c5599742a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957754"
---
# <a name="class-tab-window-properties-dialog-box"></a>Registerkarte "Klasse", Dialogfeld "Fenstereigenschaften"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verwenden der **Klasse** Tab, um Informationen für die Klasse des ausgewählten Fensters angezeigt. Zum Anzeigen der [Dialogfeld "Fenstereigenschaften"](../debugger/window-properties-dialog-box.md), Verschieben des Fokus auf die [Windows-Ansicht](../debugger/windows-view.md) Fenster. Wählen Sie einen beliebigen Knoten im Fenster in der Struktur aus, und wählen Sie dann **Eigenschaften** aus der **Ansicht** Menü.  
  
 Die folgenden Einstellungen stehen auf der **Klasse** Registerkarte:  
  
|Eingabe|Beschreibung|  
|-----------|-----------------|  
|**Klassenname**|Der Name (oder die Ordnungszahl) der Fensterklasse.|  
|**Klassenstile**|Eine Kombination von Klasse-Stil-Codes.|  
|**Klassenbytes**|Anwendungsspezifische Daten, die dieser Fensterklasse zugeordnet.|  
|**Klassenatom**|Das Atom für die Klasse, die vom der **"registerClass"** aufrufen.|  
|**Instanzhandle**|Der Instanzhandle des Moduls, das die Klasse registriert. Instanzenhandles sind nicht eindeutig.|  
|**Fensterbytes**|Die Anzahl der zusätzlichen Bytes jedes Fenster dieser Klasse zugeordnet. Die Bedeutung dieser Bytes wird von der Anwendung bestimmt. Erweitern Sie im Listenfeld aus, um die Bytewerte in DWORD-Format anzuzeigen.|  
|**Fensterprozedur**|Die aktuelle Adresse des der **WndProc** -Funktion für Windows, die von dieser Klasse. Dies unterscheidet sich von **Fensterprozedur** auf die **allgemeine** Registerkarte, wenn das Fenster als Unterklasse definiert ist.|  
|**Menüname**|Der Name des im Hauptmenü, der mit Windows dieser Klasse ("none", wenn kein Menü vorhanden ist) zugeordnet ist.|  
|**Symbolhandle**|Das Handle für das Symbol, das Windows dieser Klasse ("none", wenn es kein Symbol angezeigt wird) zugeordnet ist.|  
|**Cursorhandle**|Das Handle für den Cursor, der mit Windows dieser Klasse ("none", wenn kein Cursor vorhanden ist) zugeordnet ist.|  
|**Hintergrundpinsel**|Das Handle für den Hintergrundpinsel an, der mit Windows, die von dieser Klasse oder eine der vordefinierten COLOR_ * Farben für das Zeichnen des Fensterhintergrunds ("none", wenn kein Pinsel) zugeordnet ist.|
