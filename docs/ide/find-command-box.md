---
title: Feld „Suchen/Befehl“
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 221c5fbbd3f0f82ac97d0c2a0fcc82657e0296c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977778"
---
# <a name="findcommand-box"></a>Suchen (Feld)

Über das Feld **Find/Command** (Suchen/Befehl) können Sie nach Text suchen und Visual Studio-Befehle ausführen. Das Feld **Find/Command** (Suchen/Befehl) ist weiterhin als Steuerelement für die Symbolleiste verfügbar, wird standardmäßig aber nicht mehr angezeigt. Sie können das Feld **Find/Command** (Suchen/Befehl) einblenden, indem Sie in der Symbolleiste**Standard** auf **Schaltflächen hinzufügen oder entfernen** klicken und anschließend auf **Suchen** klicken.

Leiten Sie einen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Befehl mit einem Größer-als-Zeichen (**>**) ein, um ihn auszuführen.

Das Feld **Suchen/Befehl** speichert die letzten 20 Eingaben und zeigt sie in einer Dropdownliste an. Mithilfe der **Pfeiltasten** kann in der Liste navigiert werden.

![Suchen&#47;Befehl (Feld)](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>Suchen nach Text

Wenn Sie Text im Feld **Suchen/Befehl** angeben und dann die **EINGABETASTE** drücken, durchsucht Visual Studio standardmäßig das aktuelle Dokument oder Toolfenster mithilfe der Optionen, die im Dialogfeld **In Dateien suchen** festgelegt wurden. Weitere Informationen finden Sie unter [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md).

## <a name="entering-commands"></a>Eingeben von Befehlen

Um über das Feld **Suchen/Befehl** einen einzelnen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Befehl oder einen Alias auszugeben, anstatt nach Text zu suchen, geben Sie den Befehl mit einem vorangestellten Größer-als-Zeichen (**>**) ein. Beispiel:

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

Darüber hinaus können Sie auch das **Befehlsfenster** zum Eingeben und Ausführen von einzelnen oder mehreren Befehlen verwenden. Einige Befehle oder Aliase können eigenständig eingegeben und ausgeführt werden, für andere erfordert die Syntax die Angabe von Argumenten. Eine Liste mit Befehlen, die über Argumente verfügen, finden Sie unter [Visual Studio-Befehle](../ide/reference/visual-studio-commands.md).

## <a name="escape-characters"></a>Escapezeichen

Ein Caretzeichen (**^**) in einem Befehl bedeutet, dass das unmittelbar darauf folgende Zeichen wörtlich und nicht als Steuerzeichen interpretiert wird. Dies ermöglicht das Einbetten von geraden Anführungszeichen (**"**), Leerräumen, vorangestellten Schrägstrichen, Caretzeichen oder beliebigen anderen Literalzeichen in einen Parameter- oder Schalterwert (mit Ausnahme von Schalternamen). Beispiel:

```
>Edit.Find ^^t /regex
```

Die Funktionsweise des Caretzeichens ist unabhängig davon, ob es in Anführungszeichen eingeschlossen ist oder nicht. Wenn ein Caretzeichen das letzte Zeichen in einer Zeile ist, wird es ignoriert.

## <a name="see-also"></a>Siehe auch

- [Befehlsfenster](../ide/reference/command-window.md)
- [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)