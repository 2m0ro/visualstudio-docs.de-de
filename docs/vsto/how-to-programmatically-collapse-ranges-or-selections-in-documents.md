---
title: 'Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6174688bbab5655a7a108e1c971e926ee5977ba1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575428"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Vorgehensweise: Programmgesteuertes Reduzieren von Bereichen oder Markierungen in Dokumenten
  Wenn Sie mit einem <xref:Microsoft.Office.Interop.Word.Range> - oder <xref:Microsoft.Office.Interop.Word.Selection> -Objekt arbeiten, möchten Sie die Auswahl vor dem Einfügen von Text möglicherweise auf eine Einfügemarke setzen, um das Überschreiben vorhandenen Texts zu vermeiden. Sowohl die <xref:Microsoft.Office.Interop.Word.Range> und <xref:Microsoft.Office.Interop.Word.Selection> Objekte verfügen über eine reduzieren-Methode, die mit der die <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> -Enumerationswerte fest:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> reduziert die Auswahl auf den Anfang der Auswahl. Dies ist die Standardeinstellung, wenn Sie keinen Enumerationswert angeben möchten.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> reduziert die Auswahl auf das Ende der Auswahl.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>So reduzieren Sie einen Bereich und fügen neuen Text ein

1. Erstellen Sie ein <xref:Microsoft.Office.Interop.Word.Range> -Objekt, das aus dem ersten Absatz des Dokuments besteht.

    Das folgende Codebeispiel kann in einer Anpassung auf Dokumentebene verwendet werden.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    Das folgende Codebeispiel kann in einem VSTO-Add-In verwendet werden. In diesem Code wird das aktive Dokument verwendet.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Verwenden Sie den <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> -Enumerationswert, um den Bereich zu reduzieren.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Fügen Sie den neuen Text ein.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Wählen Sie das <xref:Microsoft.Office.Interop.Word.Range>-Steuerelement aus.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Wenn Sie den <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> -Enumerationswert verwenden, wird der Text am Anfang des folgenden Absatzes eingefügt.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Normalerweise würden Sie davon ausgehen, dass ein eingefügter neuer Satz vor der Absatzmarke eingefügt wird. Dies ist jedoch nicht der Fall, weil die Absatzmarke im ursprünglichen Bereich enthalten ist. Weitere Informationen finden Sie unter [Vorgehensweise: Programmgesteuertes Ausschließen von Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>So reduzieren Sie einen Bereich in einer Anpassung auf Dokumentebene

1. Das folgende Beispiel zeigt die vollständige Methode für eine Anpassung auf Dokumentebene. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisDocument` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Um einen Bereich in einem VSTO-Add-in zu reduzieren.

1. Das folgende Beispiel zeigt die vollständige Methode für ein VSTO-Add-in. Wenn Sie diesen Code verwenden möchten, führen Sie ihn von der `ThisAddIn` -Klasse im Projekt aus.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Programmgesteuertes Einfügen von Text in Word-Dokumente](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Vorgehensweise: Programmgesteuertes definieren und Markieren von Bereichen in Dokumenten](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Vorgehensweise: Programmgesteuertes Abrufen von Start- und Endzeit von Zeichen in Bereichen](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Vorgehensweise: Programmgesteuertes ausschließen Absatzmarken beim Erstellen von Bereichen](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Vorgehensweise: Programmgesteuertes Erweitern von Bereichen in Dokumenten](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Vorgehensweise: Programmgesteuertes Zurücksetzen von Bereichen in Word-Dokumenten](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
