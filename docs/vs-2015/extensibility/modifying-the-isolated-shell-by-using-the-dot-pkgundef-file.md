---
title: Ändern der Isolated Shell mithilfe der. Pkgundef-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3741fc9abdae6693670538c80288dfdefcefd84e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511076"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Ändern der Isolated Shell mithilfe der. Pkgundef-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Ändern der Isolated Shell durch Verwenden der. Pkgundef-Datei](https://docs.microsoft.com/visualstudio/extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file).  
  
Sie können die pkgundef-Datei zum Ausschließen von angegebenen Registrierungseinträge in einer isolierten Shell-Anwendung ändern. In der Regel kopiert beim ersten, die eine Anwendung auf einem Computer gestartet wird die Visual Studio-Shell die vorhandene Visual Studio-Registrierungseinträge in den Stamm-Registrierungsschlüssel für die Anwendung. Dies schließt alle Verweise, die derzeit installierten VSPackages.  
  
 Fügen Sie zum Ausschließen eines bestimmten Registrierungseintrags in einer isolierten Shell-Anwendung in die Anwendung-pkgundef-Datei gefolgt von der Paket-Schlüssel durch den Eintrag. Schlüssel und Einträge werden genau wie in der PKGDEF-Datei dargestellt. d. h. als [$RootKey$] oder [$RootKey$\\*Unterschlüssel*] und "*Eintrag*" =*Wert*, wobei *Unterschlüssel* der Unterschlüssel beeinflussen, *Eintrag* ist der Eintrag zu entfernen, und *Wert* ist entweder `""` oder `dword:00000000`.  
  
 Um mehrere Einträge aus einem Registrierungsschlüssel auszuschließen, sondern nur Auflisten des Schlüssels einmal, gefolgt von einer Zeile für jeden Eintrag ausschließen.  
  
 Um einen Registrierungsschlüssel für die gesamte von einer isolierten Shell-Anwendung zu auszuschließen, fügen Sie den Schlüssel in die Anwendung pkgundef-Datei, aber geben Sie keinen keine Registrierungseinträge für diesen Schlüssel an.  
  
 Sie können der pkgundef-Datei Kommentare hinzufügen. Ein einzeiliger Kommentar muss zwei Schrägstriche als die ersten beiden Zeichen aufweisen.  
  
 So entfernen Sie beispielsweise die **Herstellen einer Verbindung mit Datenbank** und **Herstellen einer Verbindung mit Server-R** von Befehlen auf die **Tools** im Menü können Sie die auskommentierung die Zeile aufheben:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 ein, und fügen Sie die Zeile:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 in der Anwendung pkgundef-Datei.  
  
## <a name="see-also"></a>Siehe auch  
 [Paket-GUIDs von Visual Studio-Funktionen](../extensibility/package-guids-of-visual-studio-features.md)   
 [Anpassen der Isolated Shell](../extensibility/customizing-the-isolated-shell.md)

