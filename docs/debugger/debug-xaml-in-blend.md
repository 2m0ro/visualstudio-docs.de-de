---
title: Debuggen von XAML in Blend | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 535e7ea155200b06b0783e79d95f4eba96ce1eed
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399521"
---
# <a name="debug-xaml-in-blend"></a>Debuggen von XAML in Blend
Verwenden Sie die Tools in [!INCLUDE[blend_first](../debugger/includes/blend_first_md.md)], um den XAML-Code in der App zu debuggen. Beim Erstellen eines Projekts werden alle Fehler im Bereich **Ergebnisse** angezeigt. Doppelklicken Sie auf einen Fehler, um das dazugehörige Markup zu suchen. Wenn Sie mehr Platz zum Arbeiten benötigen, können Sie den Bereich **Ergebnisse** durch Drücken von F12 ausblenden.

## <a name="syntax-errors"></a>Syntaxfehler
 Syntaxfehler treten auf, wenn die Formatierungsregeln der Sprache im XAML-Code oder in Code-Behind-Dateien nicht befolgt werden. Die Beschreibung des Fehlers kann bei seiner Behebung hilfreich sein. In der Liste wird auch der Name der Datei und die Nummer der Zeile angegeben, in der der Fehler auftritt. Die XAML-Fehler werden auch auf der Registerkarte **Markup** im Bereich **Ergebnisse** angezeigt.

> [!TIP]
> XAML ist eine XML-basierte Markupsprache, die XML-Syntaxregeln befolgt.

 Es folgen einige häufige Ursachen für XAML-Syntaxfehler:

- Ein Schlüsselwort wurde falsch geschrieben, oder die Groß-/Kleinschreibung ist falsch.

- Um Attribute oder um Textzeichenfolgen fehlen Anführungszeichen.

- Für ein XAML-Element fehlt ein Endtag.

- Ein XAML-Element ist an einer Position vorhanden, an der es nicht zulässig ist.

  Weitere Informationen über die allgemeine XAML-Syntax finden Sie in der [Anleitung zur grundlegenden XAML-Syntax](http://go.microsoft.com/fwlink/?LinkId=329942).

  Sie können in [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] auch einfache Code-Behind-Syntaxfehler, Kompilierungsfehler und Laufzeitfehler identifizieren und beheben. Für Code-Behind-Fehler können Sie dies allerdings möglicherweise in Visual Studio einfacher durchführen.

### <a name="debugging-sample-xaml-code"></a>Debuggen von XAML-Beispielcode
 Im folgenden Beispiel wird eine einfache XAML-Debugsitzung in [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] schrittweise beschrieben.

##### <a name="to-create-a-project"></a>So erstellen Sie ein Projekt

1. Öffnen Sie in [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] das Menü **Datei**, und klicken Sie auf **Neues Projekt**.

    Auf der linken Seite des Dialogfelds **Neues Projekt** wird eine Liste der Projekttypen angezeigt. Wenn Sie auf einen Projekttyp klicken, werden die Projektvorlagen, die diesem Typ zugeordnet sind, auf der rechten Seite angezeigt.

2. Klicken Sie in der Liste der Projekttypen auf **Windows Universal**.

3. Klicken Sie in der Liste der Projektvorlagen auf **leere App (Universelles Windows)**.

4. In der **Namen** Textfeld `DebuggingSample`.

5. Überprüfen Sie im Textfeld **Speicherort** den Projektspeicherort.

6. Klicken Sie im Listenfeld **Sprache** auf **Visual C#**, und klicken Sie dann auf **OK**, um das Projekt zu erstellen.

7. Klicken Sie mit der rechten Maustaste auf die Entwurfsoberfläche, und klicken Sie dann auf **Quelle anzeigen**, um zur Ansicht **Geteilt** zu wechseln.

8. Kopieren Sie den folgenden Code, indem Sie auf den Link **Kopieren** in der rechten oberen Ecke des Codes klicken.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. Suchen Sie das standardmäßige **Raster**, und fügen Sie den Code zwischen den **Grid**-Start- und Endtags ein. Anschließend sollte der Code ungefähr wie folgt aussehen:

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
         </Grid>
    </Grid>
    ```

10. Drücken Sie STRG+UMSCHALT+B, um das Projekt zu erstellen.

    Eine Fehlermeldung wird angezeigt, dass das Projekt nicht erstellt werden kann. Im unteren Bereich der App wird zudem der Bereich **Ergebnisse** mit der Liste der Fehler angezeigt.

    ![Debuggen von XAML in Blend für Visual Studio](../debugger/media/blend_debugxaml_xaml.png "Blend_debugXAML_XAML")

### <a name="resolving-xaml-errors"></a>Beheben von XAML-Fehlern
 Wenn XAML-Fehler ermittelt werden, zeigt die Entwurfsoberfläche eine Warnung an, dass das Projekt ungültiges Markup enthält. Während Sie die Fehler beheben, wird die Fehlerliste im Bereich **Ergebnisse** aktualisiert. Wenn Sie alle Fehler behoben haben, wird die Entwurfsoberfläche aktiviert und die App wird darin angezeigt.

##### <a name="to-resolve-the-xaml-errors"></a>So beheben Sie die XAML-Fehler

1. Doppelklicken Sie auf den ersten Fehler in der Fehlerliste. Die Beschreibung lautet: "The value '<' is not valid in an attribute." (Der Wert „<“ ist in Attributen ungültig). Wenn Sie auf den Fehler doppelklicken, ermittelt der Zeiger die entsprechende Position im Code. `<` vor `Button` ist gültig und kein Attribut, wie in der Fehlermeldung beschrieben. Wenn Sie die vorhergehende Codezeile prüfen, stellen Sie fest, dass die schließenden Anführungszeichen für das `Top`-Attribut fehlen. Geben Sie die schließenden Anführungszeichen ein. Die Fehlerliste im Bereich **Ergebnisse** wird aktualisiert, um die Änderung zu reflektieren.

2. Doppelklicken Sie auf die Beschreibung "" 0"ist nicht gültig zu Beginn eines Namens". `Margin="0,149,0,0"` wird angezeigt, um gültig zu sein. Allerdings stimmt der Farbcode für `Margin` nicht mit den anderen Instanzen von `Margin` im Code überein. Da für das vorangehende Name-Wert-Paar die schließenden Anführungszeichen fehlen (`VerticalAlignment="Top`), wird `Margin="` als Teil des Werts des vorangehenden Attributs gelesen, und 0 wird als Anfang von einem Name-Wert-Paar gelesen. Geben Sie die schließenden Anführungszeichen für `Top` ein. Die Fehlerliste im Bereich **Ergebnisse** wird aktualisiert, um die Änderung zu reflektieren.

3. Doppelklicken Sie auf den verbleibenden Fehler: "Das schließende XML-Tag 'Button' ist falsch zugeordnet." Der Zeiger befindet sich beim **Grid**-Endtag (`</Grid>`), um anzugeben, dass der Fehler mutmaßlich im `Grid`-Objekt ist. Beachten Sie, dass das Endtag für das `Button`-Objekt fehlt. Nachdem Sie das `/`-Endtag hinzugefügt haben, wird die Liste im Bereich **Ergebnisse** aktualisiert. Nach dem Beheben dieser Anfangsfehler wurden zwei weitere Fehler identifiziert.

4. Doppelklicken Sie auf: "Das Element 'content' wurde nicht erkannt, oder es kann nicht auf das Element zugegriffen werden." Das `c` in `content` muss groß geschrieben sein. Ersetzen Sie das klein geschriebene "c" durch ein groß geschriebenes "C".

5. Doppelklicken Sie auf "die Eigenschaft 'Mame' ist nicht in der '<http://schemas.microsoft.com/winfx/2006/xaml>" Namespace. " Das "M" in "Mame" muss ein "N" sein. Ersetzen Sie das "M" durch ein "N". Da der XAML-Code jetzt verarbeitet werden kann, wird die App auf der Entwurfsoberfläche angezeigt.

    ![Debuggen von XAML in Blend für Visual Studio](../debugger/media/blend_debugartboard_xaml.png "Blend_debugArtboard_XAML")

    Drücken Sie STRG+UMSCHALT+B, um das Projekt zu erstellen und zu bestätigen, dass es keine weiteren Fehler enthält.

## <a name="debugging-in-visual-studio"></a>Debuggen in Visual Studio
 Sie können [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]-Projekte in Visual Studio öffnen, um den App-Code einfacher zu debuggen. Um ein [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]-Projekt in Visual Studio zu öffnen, klicken Sie im Bereich **Projekte** mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **In Visual Studio bearbeiten**. Wenn Sie die Debugsitzung in Visual Studio abgeschlossen haben, drücken Sie STRG+UMSCHALT+S, um sämtliche Änderungen zu speichern, und wechseln Sie anschließend zurück zu [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)]. Sie werden aufgefordert, das Projekt erneut zu laden. Klicken Sie auf **Ja, alle**, um in [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] weiterzuarbeiten.

 Weitere Informationen zum Debuggen von Apps finden Sie unter [Debuggen von UWP-apps in Visual Studio](http://go.microsoft.com/fwlink/?LinkId=329944).

## <a name="getting-help"></a>Hilfe zu weiteren Fragen
 Bei Bedarf weitere Unterstützung zum Debuggen Ihrer [!INCLUDE[blend_subs](../debugger/includes/blend_subs_md.md)] -app, die Sie suchen den [UWP-app – Foren](http://go.microsoft.com/fwlink/?LinkId=280308) für Beiträge konkreten Problem oder eine Frage.
