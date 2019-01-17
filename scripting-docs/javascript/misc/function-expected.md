---
title: Funktion erwartet. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2db3e95d4baece288c9f984a7a9cf7a82c9d1d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349802"
---
# <a name="function-expected"></a>Funktion erwartet
Entweder Sie haben versucht, zum Aufrufen einer der **Funktionsprototyp** Methoden für ein Objekt, das nicht war eine `Function` -Objekt, oder Sie ein Objekt im Kontext eines Funktionsaufrufs verwendet. Der folgende Code erzeugt z. B. diesen Fehler, da **Beispiel** ist keine Funktion.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
-   Rufen Sie nur **Funktionsprototyp** Methoden `Function` Objekte.  
  
-   Stellen Sie sicher, dass Sie den Funktionsaufruf-Operator verwenden `()` nur Funktionen aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Function-Objekt](../../javascript/reference/function-object-javascript.md)   
 [prototype-Eigenschaft (Objekt)](../../javascript/reference/prototype-property-object-javascript.md)