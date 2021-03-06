---
title: BeginCapture | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e714245ff2585f9de0b998160ce08f04c88b097
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896435"
---
# <a name="begincapture"></a>BeginCapture
Startet ein Erfassungsintervall, das mit `EndCapture` endet.

## <a name="syntax"></a>Syntax

```C++
void BeginCapture();
```

## <a name="remarks"></a>Hinweise
 Ein Erfassungsintervall umfasst in der Regel eine Teilmenge eines Frames, etwa wenn Sie Grafikinformationen nur über eine bestimmte Art von Zeichnen-Befehl erfassen möchten. Wenn das Erfassungsintervall einen Aufruf von "Present" umfasst, dann werden zwei Frames von Grafikinformationen erfasst. Der erste Frame umfasst das Intervall zwischen dem Aufruf von `BeginCapture` und dem Aufruf von "Present". Das zweite Intervall umfasst das Intervall zwischen dem ersten Direct3D-Ereignis nach dem Aufruf von "Present" und dem Aufruf von `EndCapture`.

 Um ein Intervall zu erfassen, müssen Sie Ihrer app erfassen und Aufzeichnen von Grafikinformationen vorbereiten, d. h. Sie aufgerufen hat, [Init](init.md) durch eine Instanz der dem `VsgDbg` -Klasse vor dem Aufruf `BeginCapture` oder `EndCapture`.

## <a name="see-also"></a>Siehe auch
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)