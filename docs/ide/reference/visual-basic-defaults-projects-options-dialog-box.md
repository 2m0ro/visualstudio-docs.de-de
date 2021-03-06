---
title: VB-Standard, Projekte, Dialogfeld "Optionen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5aedaf5c31eca900ec1730622dfc7ff6f026a61a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62789134"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>VB-Standard, Projekte, Dialogfeld "Optionen"
Legt die Standardeinstellungen für Visual Basic-Projekteinstellungen fest. Beim Erstellen eines neuen Projekts werden die angegebenen Optionsanweisungen dem Projektheader im Code-Editor hinzugefügt. Die Optionen werden für alle Visual Basic-Projekte verwendet.

 Klicken Sie zum Zugriff auf dieses Dialogfeld im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Projekte und Projektmappen**, und klicken Sie auf **VB-Standard**.

 **Option Explicit**

 Legt als Compilerstandardeinstellung fest, dass explizite Deklarationen von Variablen erforderlich sind. Standardmäßig wird für **Option Explicit** der Wert **On** festgelegt. Weitere Informationen finden Sie unter [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

 **Option Strict**

 Legt als Compilerstandardeinstellung fest, dass explizite einschränkende Konvertierungen erforderlich sind und eine späte Bindung nicht zulässig ist. Standardmäßig wird für **Option Strict** der Wert **Off** festgelegt. Weitere Informationen finden Sie unter [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

 **Option Compare**

 Legt als Compilerstandardeinstellung für Vergleiche von Zeichenfolgen entweder „binary“ (Groß- und Kleinschreibung wird beachtet) oder „text“ (Groß- und Kleinschreibung wird nicht beachtet) fest. Standardmäßig wird für **Option Compare** der Wert **binary** festgelegt. Weitere Informationen finden Sie unter [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

 **Option Infer**

 Legt die Compilerstandardeinstellung für den lokalen Typrückschluss fest. Standardmäßig wird für **Option Infer** der Wert **On** für neu erstellte Projekte und **Off** für migrierte Projekte verwendet, die in früheren Versionen von Visual Basic erstellt wurden. Weitere Informationen finden Sie unter [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

## <a name="see-also"></a>Siehe auch

- [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)