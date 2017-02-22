---
title: "Registrieren ein Toolfenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Toolfenster, verwaltete registrieren"
  - "Toolfenster, registrieren"
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrieren ein Toolfenster
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Toolfenster mit einer registrieren <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> und  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## Beispiel  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 Im obigen Code die <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> registriert das Toolfenster PersistedWindowPane und DynamicWindowPane mit Visual Studio. Der beibehaltenen Toolfenster angedockt und im Registerkartenformat mit **Projektmappen\-Explorer**, und das dynamische Fenster erhält ein Standardthema zum Starten von Position und Größe. Fenster Dynamische vorübergehender Natur, erfolgt die angibt, dass er beim Start nicht erstellt wird. Schreibt einen Wert DontForceCreate im ToolWindows Schlüssel in der Registrierung. Weitere Informationen finden Sie unter [Tool\-Fenster Anzeigekonfiguration](../extensibility/tool-window-display-configuration.md).