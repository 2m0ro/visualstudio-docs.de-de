---
title: "BYTES_PER_ELEMENT-Konstante (Float64Array) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e1afc629-4df3-49ce-baf5-5b51a6340621
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# BYTES_PER_ELEMENT-Konstante (Float64Array)
Die Größe jedes Elements im Array in Bytes.  
  
## Syntax  
  
```javascript  
var arraySize = int8Array.BYTES_PER_ELEMENT;  
```  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie die Größe der Arrayelemente abgerufen wird.  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            alert(floatArr.BYTES_PER_ELEMENT);  
        }  
    }  
  
```  
  
## Anforderungen  
 [!INCLUDE[jsv10](../../includes/jsv10-md.md)]