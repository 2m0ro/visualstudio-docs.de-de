---
title: Hinzufügen von Visual Studio-Befehlen zu einer Startseite | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 638c9c0f0d024830124445485dcf9991678bd4d7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63429016"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Hinzufügen von Visual Studio-Befehlen zu einer Startseite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine benutzerdefinierte Startseite erstellen, können Sie Visual Studio-Befehle, hinzufügen. Dieses Dokument erläutert die verschiedenen Möglichkeiten, Visual Studio-Befehle für XAML-Objekte auf einer Startseite zu binden.  
  
 Weitere Informationen über Befehle in XAML finden Sie unter [Befehlsübersicht](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Hinzufügen von Befehlen aus dem Befehl auch  
 Die Startseite im erstellt [erstellen eine benutzerdefinierte Startseite](../extensibility/creating-a-custom-start-page.md) hinzugefügt der <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> und <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> Namespaces wie folgt.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Fügen Sie einen anderen Namespace aus der Assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll für Microsoft.VisualStudio.Shell hinzu. (Möglicherweise müssen Sie einen Verweis auf diese Assembly in Ihrem Projekt hinzufügen.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Können Sie die `vscom:` Alias zum Binden von Visual Studio-Befehle an der XAML-Steuerelemente auf der Seite durch Festlegen der <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Eigenschaft des Steuerelements `vscom:VSCommands.ExecuteCommand`. Sie können dann Festlegen der <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> -Eigenschaft auf den Namen des Befehls zum Ausführen wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
> Die `x:` Alias, der dem XAML-Schema verweist, muss sich am Anfang aller Befehle.  
  
 Legen Sie den Wert von der `Command` Eigenschaft, um solche Befehle, die aus zugegriffen werden kann die **Befehl** Fenster. Eine Liste der verfügbaren Befehle, finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).  
  
 Wenn Sie der Befehl zum Hinzufügen zusätzlichen Parameter erfordert, können Sie es hinzufügen, auf den Wert des der `CommandParameter` Eigenschaft. Separate Parameter von Befehlen mithilfe von Speicherplätzen, wie im folgenden Beispiel gezeigt.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Aufrufen von Erweiterungen auch aus dem Befehl  
 Sie können die Befehle von registrierte VSPackages aufrufen, indem Sie mit derselben Syntax, die verwendet wird, um andere Visual Studio-Befehle aufrufen. Wenn eine installierte VSPackage fügt z. B. eine **auf der Startseite** Befehl die **Ansicht** im Menü können Sie diesen Befehl aufrufen, indem Sie die Einstellung `CommandParameter` zu `View.HomePage`.  
  
> [!NOTE]
> Wenn Sie einen Befehl, der ein VSPackage zugeordnet ist aufrufen, muss das Paket geladen werden, wenn der Befehl aufgerufen wird.  
  
## <a name="adding-commands-from-assemblies"></a>Hinzufügen von Befehlen von Assemblys  
 Zum Aufrufen eines Befehls an, aus einer Assembly oder den Zugriff von Code in einem VSPackage, die nicht mit einem Menübefehl zugeordnet ist, müssen Sie erstellen Sie einen Alias für die Assembly und rufen Sie dann auf den Alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Zum Aufrufen eines Befehls aus einer assembly  
  
1. Fügen Sie einen Verweis auf die Assembly, in der Projektmappe.  
  
2. Fügen Sie am Anfang der Datei "StartPage.xaml" eine Direktive für die Assembly hinzu, wie im folgenden Beispiel gezeigt.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Rufen Sie den Befehl durch Festlegen der `Command` Eigenschaft eines XAML-Objekts, wie im folgenden Beispiel gezeigt.  
  
     Xaml  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> Sie müssen die Kopie der Assembly und fügen Sie ihn in... \\ *Visual Studio-Installationsordner*\Common7\IDE\PrivateAssemblies\ um sicherzustellen, dass es geladen wird, bevor sie aufgerufen wird.  
  
## <a name="adding-commands-with-the-dte-object"></a>Hinzufügen von Befehlen mit dem DTE-Objekt  
 Sie können das DTE-Objekt auf einer Startseite auf, sowohl im Markup als auch im Code zugreifen.  
  
 Im Markup, Sie können darauf zugreifen, indem mithilfe der [Binding als Markuperweiterung](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) Syntax zum Aufrufen der <xref:EnvDTE.DTE> Objekt. Sie können diesen Ansatz verwenden, um an einfache Eigenschaften, z. B. die Bindung, die Auflistungen zurückgeben, aber Sie können nicht gebunden werden, um Methoden oder Dienste. Das folgende Beispiel zeigt eine <xref:System.Windows.Controls.TextBlock> -Steuerelement, das gebunden wird die <xref:EnvDTE._DTE.Name%2A> -Eigenschaft, und ein <xref:System.Windows.Controls.ListBox> -Steuerelement, das Listet die <xref:EnvDTE.Window.Caption%2A> Eigenschaften der Auflistung, die von zurückgegeben wird die <xref:EnvDTE._DTE.Windows%2A> Eigenschaft.  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Ein Beispiel finden Sie unter [Exemplarische Vorgehensweise: Speichern von Benutzereinstellungen auf einer Startseite](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen eines Benutzersteuerelements zur Startseite](../extensibility/adding-user-control-to-the-start-page.md)
