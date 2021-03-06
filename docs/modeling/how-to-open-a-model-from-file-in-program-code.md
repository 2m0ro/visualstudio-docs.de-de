---
title: 'Vorgehensweise: Öffnen eines Modells aus einer Datei im Programmcode'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 092af518cc6c6fb1d98025cda54a6a1d491940c9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445136"
---
# <a name="how-to-open-a-model-from-file-in-program-code"></a>Vorgehensweise: Öffnen eines Modells aus einer Datei im Programmcode
Sie können die DSL-Modelle in einer beliebigen Anwendung öffnen.

 Aus einer Visual Studio-Erweiterung können Sie ModelBus zu diesem Zweck verwenden. ModelBus stellt Standardmechanismus zum Verweisen auf ein Modell oder Elemente in einem Modell, und klicken Sie für die Suche nach dem Modell, wenn es verschoben wurde. Weitere Informationen finden Sie unter [Integrieren von Modellen mithilfe von Visual Studio-Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="target-framework"></a>Zielframework
 Legen Sie die **Zielframework** Ihres Anwendungsprojekts zum **.NET Framework 4**.

#### <a name="to-set-the-target-framework"></a>Um das Zielframework festzulegen.

1. Öffnen Sie Visual Studio-Projekt für die Anwendung, in der Sie ein DSL-Modell lesen möchten.

2. In **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**.

3. Im Fenster für die Projekteigenschaften auf die **Anwendung** Registerkarte die **Zielframework** Feld **.NET Framework 4**.

> [!NOTE]
> Müssen Sie möglicherweise dazu, auch wenn Sie **.NET Framework 4** in das Dialogfeld für die Erstellung des Projekts. Das Zielframework sollte nicht **.NET Framework 4 Client Profile**.

## <a name="references"></a>Verweise
 Sie müssen diese Verweise zu Ihrem Visual Studio-Webanwendungsprojekt hinzuzufügen:

- `Microsoft.VisualStudio.Modeling.Sdk.11.0`

    - Wenn diese nicht angezeigt wird der **.NET** Registerkarte die **Verweise hinzufügen** im Dialogfeld klicken Sie auf die **Durchsuchen** Registerkarte, und navigieren Sie zu `%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Common\Assemblies\`.

- Die DSL-Assembly, die sich unter dem Ordner "Bin" Ihrem DSL-Projekt werden. Der Name hat in der Regel Folgendes Format: *Ihrunternehmen*. *IhrProjekt*`.Dsl.dll`.

## <a name="important-classes-in-the-dsl"></a>Wichtige Klassen in der DSL
 Bevor Sie den Code, der Ihre DSL liest schreiben können, sollten Sie die Namen einiger der von Ihrer DSL generierten Klassen wissen. Öffnen Sie in der DSL-Projektmappe, die **Dsl** Projekt, und suchen Sie in der **GeneratedCode** Ordner. Doppelklicken Sie alternativ auf die DSL-Assembly in Ihrem Projekt **Verweise**, und öffnen Sie in den DSL-Namespace **Objektkatalog**.

 Dies sind die Klassen, die gekennzeichnet werden sollen:

- *YourDslRootClass* – Dies ist der Name der Stammklasse in Ihre `DslDefinition.dsl`.

- *Ihrdslname* `SerializationHelper` – diese Klasse wird definiert, `SerializationHelper.cs` in Ihrem DSL-Projekt.

- *Ihrdslname* `DomainModel` – diese Klasse wird definiert, `DomainModel.cs` in Ihrem DSL-Projekt.

## <a name="reading-from-a-file"></a>Lesen aus einer Datei
 Im folgende Beispiel wird entworfen, um eine DSL Lesen in der zu die wichtigsten Klassen wie folgt:

- FamilyTreeModel

- FamilyTreeSerializationHelper

- FamilyTreeDomainModel

  Die andere Domänenklasse in diese DSL ist die Person.

```csharp
using System;
using Microsoft.VisualStudio.Modeling;
using Company.FamilyTree; // Your DSL namespace

namespace StandaloneReadDslConsole
{ class Program
  { static void Main(string[] args)
    {
      // The path of a DSL model file:
      string dslModel = @"C:\FamilyTrees\Tudor.ftree";
      // Set up the Store to read your type of model:
      Store store = new Store(
        typeof(Company.FamilyTree.FamilyTreeDomainModel));
      // The Model type generated by the DSL:
      FamilyTreeModel familyTree;
      // All Store changes must be in a Transaction:
      using (Transaction t =
        store.TransactionManager.BeginTransaction("Load model"))
      {
        familyTree =
           FamilyTreeSerializationHelper.Instance.
              LoadModel(store, dslModel, null, null, null);
        t.Commit(); // Don't forget this!
      }
      // Now we can read the model:
      foreach (Person p in familyTree.People)
      {
        Console.WriteLine(p.Name);
        foreach (Person child in p.Children)
        {
          Console.WriteLine("    " + child.Name);
        }
} } } }
```

## <a name="saving-to-a-file"></a>In einer Datei speichern
 Dem folgenden Zusatz zu den vorherigen Code bewirkt eine Änderung des Modells, und klicken Sie dann in eine Datei gespeichert.

```csharp
using (Transaction t =
  store.TransactionManager.BeginTransaction("update model"))
{
  // Create a new model element:
  Person p = new Person(store);
  // Set its embedding relationship:
  p.FamilyTreeModel = familyTree;
  // - same as: familyTree.People.Add(p);
  // Set its properties:
  p.Name = "Edward VI";
  t.Commit(); // Don't forget this!
}
// Save the model:
try
{
  SerializationResult result = new SerializationResult();
  FamilyTreeSerializationHelper.Instance
    .SaveModel(result, familyTree, @"C:\FamilyTrees\Tudor-upd.ftree");
  // Report any error:
  if (result.Failed)
  {
    foreach (SerializationMessage message in result)
    {
      Console.WriteLine(message);
    }
  }
}
catch (System.IO.IOException ex)
{ ... }
```