---
title: Auswählen einer Strategie für die ClickOnce-Aktualisierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application updates, ClickOnce
- updates, ClickOnce
- ClickOnce deployment, update strategies
ms.assetid: d8b6e7bb-4ea0-47f3-91cd-48580bdceccc
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8215b8e0955b79224341d5d43b51a473740f5fe5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442335"
---
# <a name="choosing-a-clickonce-update-strategy"></a>Auswählen einer Strategie für die ClickOnce-Aktualisierung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] kann automatische Anwendungsupdates bereitstellen. Eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendung liest in regelmäßigen Abständen die Bereitstellungsmanifestdatei, um zu prüfen, ob Anwendungsupdates verfügbar sind. Falls verfügbar, wird die neue Version der Anwendung heruntergeladen und ausgeführt. Aus Leistungsgründen werden nur die Dateien heruntergeladen, die sich geändert haben.  
  
 Beim Entwerfen einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendung müssen Sie bestimmen, welche Strategie die Anwendung bei der Suche nach verfügbaren Updates verfolgen soll. Es gibt drei grundlegende Strategien: Suchen nach Updates beim Anwendungsstart, Suchen nach Updates nach dem Anwendungsstart (in einem Thread im Hintergrund) oder Bereitstellen einer Benutzeroberfläche für Updates.  
  
 Außerdem können Sie bestimmen, wie oft die Anwendung nach Updates suchen soll, und Sie können Updates als obligatorisch kennzeichnen.  
  
> [!NOTE]
> Für Anwendungsupdates ist eine Netzwerkverbindung erforderlich. Wenn keine Netzwerkverbindung vorhanden ist, wird die Anwendung unabhängig von der ausgewählten Updatestrategie ausgeführt, ohne nach Updates zu suchen.  
  
> [!NOTE]
> Immer, wenn die Anwendung in .NET Framework 2.0 and .NET Framework 3.0 vor oder nach dem Start bzw. unter Verwendung der <xref:System.Deployment.Application>-APIs nach Updates sucht, muss `deploymentProvider` im Bereitstellungsmanifest festgelegt werden. Das `deploymentProvider`-Element entspricht in Visual Studio dem Feld **Updatepfad**, das sich im Dialogfeld **Updates** der Registerkarte **Veröffentlichen** befindet. Diese Regel wird in .NET Framework 3.5 gelockert. Weitere Informationen finden Sie unter [Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
## <a name="checking-for-updates-after-application-startup"></a>Suchen nach Updates nach dem Anwendungsstart  
 Bei dieser Strategie versucht die Anwendung während der Ausführung, die Datei mit dem Bereitstellungsmanifest im Hintergrund aufzufinden und zu lesen. Wenn ein Update verfügbar ist, wird der Benutzer beim nächsten Ausführen der Anwendung aufgefordert, das Update zu herunterladen und zu installieren.  
  
 Diese Strategie funktioniert am besten bei Netzwerkverbindungen mit niedriger Bandbreite oder größeren Anwendungen, die lange Downloads erfordern könnten.  
  
 Um diese Updatestrategie zu aktivieren, klicken Sie im Dialogfeld **Anwendungsupdates** im Bereich **Zeitpunkt auswählen, wann die Anwendung auf Updates überprüfen soll** auf **Nach dem Starten der Anwendung**. Geben Sie dann im Abschnitt **Häufigkeit der Überprüfung auf Updates angeben** ein Updateintervall an.  
  
 Dies entspricht der im Folgenden dargestellten Änderung des **Update**-Elements im Bereitstellungsmanifest:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <expiration maximumAge="6" unit="hours" />  
   </update>  
</subscription>  
```  
  
## <a name="checking-for-updates-before-application-startup"></a>Suchen nach Updates vor dem Anwendungsstart  
 Bei der Standardstrategie wird versucht, die Datei mit dem Bereitstellungsmanifest vor dem Starten der Anwendung aufzufinden und zu lesen. Bei dieser Strategie versucht die Anwendung jedes Mal, wenn der Benutzer die Anwendung startet, die Datei mit dem Bereitstellungsmanifest aufzufinden und zu lesen. Wenn ein Update verfügbar ist, wird es heruntergeladen und gestartet. Andernfalls wird die vorhandene Version der Anwendung gestartet.  
  
 Diese Strategie funktioniert am besten bei Netzwerkverbindungen mit hoher Bandbreite. Bei Verbindungen mit niedriger Bandbreite ist die Verzögerung beim Anwendungsstart möglicherweise nicht akzeptabel.  
  
 Um diese Updatestrategie zu aktivieren, klicken Sie im Dialogfeld **Anwendungsupdates** im Bereich **Zeitpunkt auswählen, wann die Anwendung auf Updates überprüfen soll** auf **Vor Start der Anwendung**.  
  
 Dies entspricht der im Folgenden dargestellten Änderung des **Update**-Elements im Bereitstellungsmanifest:  
  
```  
<!-- When to check for updates -->  
<subscription>  
   <update>  
      <beforeApplicationStartup />  
   </update>  
</subscription>  
```  
  
## <a name="making-updates-required"></a>Kennzeichnen von Updates als obligatorisch  
 In bestimmten Situationen ist es erforderlich, dass die Benutzer ausschließlich eine aktualisierte Version der Anwendung ausführen. Angenommen, Sie nehmen eine Änderung an einer externen Ressource vor, z. B. an einem Webdienst, aufgrund derer die ältere Version der Anwendung nicht mehr ordnungsgemäß funktioniert. In dieser Situation würden Sie das Update als obligatorisch kennzeichnen und damit verhindern, dass Benutzer die ältere Version ausführen.  
  
> [!NOTE]
> Auch wenn mit den anderen Updatestrategien Updates als obligatorisch gekennzeichnet werden können, ist es nur mit der Aktivierung von **Vor Start der Anwendung** möglich, das Ausführen einer älteren Version zu verhindern. Wenn das obligatorische Update beim Start ermittelt wird, muss der Benutzer entweder das Update akzeptieren oder die Anwendung schließen.  
  
 Um ein Update als obligatorisch zu kennzeichnen, klicken Sie im Dialogfeld **Anwendungsupdates** auf **Geben Sie die mindestens erforderliche Version für diese Anwendung an**. Geben Sie anschließend die Veröffentlichungsversion an (**Hauptversion**, **Nebenversion**, **Build**, **Revision**). Sie gibt die niedrigste Versionsnummer der Anwendung an, die installiert werden kann.  
  
 Dies entspricht dem Festlegen des **minimumRequiredVersion**-Attributs des **Deployment**-Elements im Bereitstellungsmanifest, z.B.:  
  
```  
<deployment install="true" minimumRequiredVersion="1.0.0.0">  
```  
  
## <a name="specifying-update-intervals"></a>Angeben von Updateintervallen  
 Sie können auch angeben, wie oft die Anwendung nach Updates sucht. Geben Sie dazu an, dass die Anwendung nach dem Starten nach Updates suchen soll, wie zuvor in "Suchen nach Updates nach dem Anwendungsstart" beschrieben.  
  
 Um das Updateintervall anzugeben, legen Sie im Dialogfeld **Anwendungsupdates** die Eigenschaften unter **Häufigkeit der Überprüfung auf Updates angeben** fest.  
  
 Dies entspricht dem Festlegen des **maximumAge**- und **unit**-Attributs des **Update**-Elements im Bereitstellungsmanifest.  
  
 So können Sie beispielsweise angeben, dass die Anwendung bei jedem Ausführen, einmal die Woche oder einmal im Monat eine Überprüfung durchführt. Wenn zum angegebenen Zeitpunkt keine Netzwerkverbindung vorhanden ist, wird die Suche nach Updates beim nächsten Ausführen der Anwendung durchgeführt.  
  
## <a name="providing-a-user-interface-for-updates"></a>Bereitstellen einer Benutzeroberfläche für Updates  
 Bei dieser Strategie stellt der Anwendungsentwickler eine Benutzeroberfläche bereit, in der Benutzer auswählen können, wann und wie oft die Anwendung nach Updates sucht. So können Sie z. B. ein Menüelement "Jetzt auf Updates überprüfen" oder ein Dialogfeld "Updateeinstellungen" mit Auswahlmöglichkeiten für unterschiedliche Updateintervalle bereitstellen. Die APIs für die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Bereitstellung ermöglichen es, eine eigene Benutzeroberfläche für Updates zu erstellen. Weitere Informationen finden Sie unter den Ausführungen zum <xref:System.Deployment.Application>-Namespace.  
  
 Wenn eine Anwendung Bereitstellungs-APIs zur Steuerung einer eigenen Updatelogik verwendet, sollten Sie die Suche nach Updates blockieren, wie im folgenden Abschnitt unter "Verhindern der Suche nach Updates" beschrieben.  
  
 Diese Strategie funktioniert am besten, wenn Sie unterschiedliche Updatestrategien für unterschiedliche Benutzer vorsehen möchten.  
  
## <a name="blocking-update-checking"></a>Verhindern der Suche nach Updates  
 Sie können die Anwendung auch daran hindern, nach Updates zu suchen. Dies kann beispielsweise der Fall sein, wenn eine einfache Anwendung nie aktualisiert wird, Sie aber die einfache Installation der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Bereitstellung nutzen möchten.  
  
 Außerdem sollten Sie die Suche nach Updates deaktivieren, wenn eine Anwendung Bereitstellungs-APIs für die Ausführung eigener Updates verwendet; siehe "Bereitstellen einer Benutzeroberfläche für Updates" weiter oben in diesem Thema.  
  
 Um die Suche nach Updates zu verhindern, deaktivieren Sie im Dialogfeld „Anwendungsupdates“ das Kontrollkästchen **Die Anwendung soll nach Updates suchen**.  
  
 Sie können die Suche nach Updates auch verhindern, indem Sie das `<Subscription>`-Tag aus dem Bereitstellungsmanifest entfernen.  
  
## <a name="permission-elevation-and-updates"></a>Berechtigungserweiterung und Updates  
 Wenn eine neue Version einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Anwendung für die Ausführung eine höhere Vertrauensebene als die vorherige Version erfordert, wird der Benutzer durch [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] in einer Eingabeaufforderung gefragt, ob die Anwendung diese höhere Vertrauensebene erhalten soll. Wenn der Benutzer das Gewähren der höheren Vertrauensebene ablehnt, wird das Update nicht installiert. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] fordert den Benutzer beim nächsten Start auf, die Anwendung wieder zu installieren. Wenn der Benutzer zu diesem Zeitpunkt die höhere Vertrauensebene nicht gewährt und das Update nicht als erforderlich gekennzeichnet ist, wird die alte Version der Anwendung ausgeführt. Ist das Update jedoch erforderlich, wird die Anwendung erst wieder ausgeführt, wenn der Benutzer die höhere Vertrauensebene akzeptiert.  
  
 Wenn Sie die Bereitstellung vertrauenswürdiger Anwendungen verwenden, wird keine Eingabeaufforderung für Vertrauensebenen angezeigt. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Deployment.Application>   
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Auswählen einer Strategie für die ClickOnce-Bereitstellung](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Wie ClickOnce Anwendungsupdates ausführt](../deployment/how-clickonce-performs-application-updates.md)   
 [Vorgehensweise: Verwalten von Aktualisierungen für eine ClickOnce-Anwendung](../deployment/how-to-manage-updates-for-a-clickonce-application.md)
