---
title: 'Schritt 5: Bereitstellen Ihrer ASP.NET Core-App in Azure'
description: Stellen Sie Ihre ASP.NET Core-Web-App mit diesem Videotutorial und schrittweisen Anweisungen in Azure bereit.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 2d995818ec5b8ac01c9776bbf2290da39d2cc40b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970930"
---
# <a name="step-5-deploy-your-aspnet-core-app-to-azure"></a>Schritt 5: Bereitstellen Ihrer ASP.NET Core-App in Azure

Um Ihre ASP.NET Core-App und ihre Datenbank in Azure bereitzustellen, gehen Sie wie folgt vor.

_Schauen Sie sich dieses Video an, und stellen Sie wie dort gezeigt Ihre erste ASP.NET Core-App in Azure bereit._

> [!VIDEO https://www.youtube.com/embed/n8wz_f5_4wI]

## <a name="open-your-project"></a>Öffnen Ihres Projekts

Öffnen Sie Ihre ASP.NET Core-App in Visual Studio 2019. Die App sollte bereits das Setup mit EF Core und einer funktionierenden Web-API verwenden, wie in [Schritt 4 dieser Tutorialreihe](tutorial-aspnet-core-ef-step-04.md) konfiguriert.

## <a name="publish-to-azure-app-service"></a>Veröffentlichen in Azure App Service

Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Veröffentlichen** aus. Übernehmen Sie die Standardeinstellungen von **App Service** und **Neu erstellen**, und klicken Sie auf die Schaltfläche **Veröffentlichen**. Wenn Sie noch kein Azure-Konto haben, klicken Sie auf **Kostenloses Azure-Konto erstellen**, und schließen Sie den kurzen Registrierungsvorgang ab.

Fügen Sie eine SQL Server-Instanz hinzu. Geben Sie einen Administratornamen und ein Kennwort an.

![Visual Studio 2019 – Erstellen einer Azure SQL Server-Instanz](media/vs-2019/vs2019-azure-sql-server.png)

Fügen Sie Application Insights hinzu.

Klicken Sie auf die Schaltfläche **Erstellen**, um den Vorgang fortzusetzen.

![Visual Studio 2019 – Erstellen einer neuen Azure App Service-Instanz](media/vs-2019/vs2019-azure-create-new-app-service.png)

## <a name="exploring-the-azure-portal-and-your-hosted-app"></a>Untersuchen des Azure-Portals und Ihrer gehosteten App

Sobald die App Service-Instanz erstellt ist, wird Ihre Website in einem Browser gestartet. Während sie geladen wird, können Sie auch den App Service im Azure-Portal finden. Untersuchen Sie die verfügbaren Optionen für Ihre App Service-Instanz. Im Abschnitt **Übersicht** können Sie die App starten und beenden.

![Azure App Service-Optionen](media/vs-2019/vs2019-azure-app-service-menu-options.png)

### <a name="scalability"></a>Skalierbarkeit

Sie können sowohl die Optionen zum zentralen als auch horizontalen Hochskalieren der App untersuchen. Beim zentralen Hochskalieren werden die Ressourcen heraufgesetzt, die jeder Instanz zugewiesen werden, die Ihre App hostet. Beim horizontalen Hochskalieren wird die Anzahl der Instanzen heraufgesetzt, die Ihre App hosten. Sie können die automatische Skalierung für Ihre App konfigurieren, die automatisch die Anzahl der Instanzen heraufsetzt, die als Reaktion auf die Last zum Hosten Ihrer App verwendet werden, und diese dann reduzieren, sobald die Last abgenommen hat.

### <a name="security-and-compliance"></a>Sicherheit und Konformität

Weitere Vorteile des Hostens unserer App mithilfe von Azure sind Sicherheit und Compliance. Azure App Service bietet Compliance mit ISO, SOC und PCI. Wir können wahlweise Benutzer mit Azure Active Directory oder Anmeldungen per sozialem Netzwerk wie Twitter, Facebook, Google oder Microsoft authentifizieren. Wir können IP-Einschränkungen erstellen, Dienstidentitäten verwalten, benutzerdefinierte Domänen hinzufügen und SSL für die App unterstützen sowie Sicherungen mit wiederherstellbaren Archivkopien von Inhalt, Konfiguration und Datenbank der App konfigurieren. Der Zugriff auf diese Funktionen erfolgt über die Menüoptionen „Authentifizierung“ / „Autorisierung“, „Identität“, „Sicherungen“ und „SSL-Einstellungen“.

### <a name="deployment-slots"></a>Bereitstellungsslots

Wenn Sie eine App bereitstellen, tritt häufig eine kurzzeitige Downtime auf, während die App neu gestartet wird. Bereitstellungsslots vermeiden dieses Problem, indem sie Ihnen ermöglichen, eine separate Staginginstanz oder einen Satz von Instanzen bereitzustellen und diese vor dem Wechsel in die Produktion aufzuwärmen. Der Wechsel ist nur eine sofortige und nahtlose Umleitung des Datenverkehrs. Wenn in der Produktion nach dem Wechsel Probleme auftreten, können Sie immer wieder in den letzten bekannten guten Produktionszustand zurückwechseln.

## <a name="update-connection-string"></a>Aktualisieren der Verbindungszeichenfolge

Standardmäßig erwartet Azure, das zur Verbindung einer neuen App mit der neuen Instanz von SQL Server-Datenbank eine Verbindungszeichenfolge mit dem Namen `DefaultConnection` verwendet wird. Derzeit verwendet die App, die wir zuvor in dieser Tutorialreihe erstellt haben, eine Verbindungszeichenfolge mit dem Namen `AppDbContext`. Wir müssen dies in *appSettings.json* und *Startup.cs* ändern und dann die App erneut bereitstellen.

## <a name="test-the-app-running-in-azure"></a>Testen der in Azure ausgeführten App

Navigieren Sie zum */Games*-Pfad, und Sie sollten in der Lage sein, ein neues Spiel hinzuzufügen, sodass es in der Liste angezeigt wird. Navigieren Sie anschließend zum */swagger*-Pfad, und Sie sollten in der Lage sein, von dort aus die Web-API-Endpunkte zu verwenden, um zu bestätigen, dass die API der App gut funktioniert.

Herzlichen Glückwunsch! Sie haben diese Videotutorialsreihe abgeschlossen!

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr darüber, wie Sie ASP.NET Core-Anwendungen mit diesen kostenlosen Ressourcen entwerfen können.

[ASP.NET Core-Anwendungsarchitektur](https://dotnet.microsoft.com/learn/web/aspnet-architecture)

## <a name="see-also"></a>Siehe auch

- [Veröffentlichen einer ASP.NET Core-App in Azure mit Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?view=aspnetcore-2.2)