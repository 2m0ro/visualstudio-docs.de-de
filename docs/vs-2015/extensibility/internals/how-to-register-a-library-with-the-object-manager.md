---
title: 'Vorgehensweise: Registrieren einer Bibliothek mit der Objekt-Manager | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c40c695a912e97269263ba14747b72382847324d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042462"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Vorgehensweise: Registrieren einer Bibliothek beim Objekt-Manager
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tools zum Durchsuchen von Symbolen, z. B. **Klassenansicht**, **Objektkatalog**, **Aufrufbrowser** und **Ergebnisse der Symbolsuche**, können Sie anzeigen Symbole in Ihrem Projekt oder in externen Komponenten. Die Symbole enthalten Namespaces, Klassen, Schnittstellen, Methoden und anderen Sprachelemente. Die Bibliotheken diese Symbole verfolgen und verfügbar zu machen, damit die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Objekt-Manager, die die Tools mit den Daten auffüllt.  
  
 Der Objekt-Manager verfolgt des aller verfügbare Bibliotheken. Jede Bibliothek muss mit der Objekt-Manager registrieren, bevor Sie die Symbole für die Tools zum Durchsuchen von Symbolen bereitstellen.  
  
 In der Regel, registrieren Sie eine Bibliothek aus, wenn eine VSPackage geladen. Allerdings kann es zu einem späteren Zeitpunkt erfolgen nach Bedarf. Sie aufheben die Bibliothek, wenn das VSPackage wird heruntergefahren.  
  
 Verwenden Sie zum Registrieren einer Bibliotheks die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> Methode. Verwenden Sie im Fall von verwaltetem Code-Bibliothek, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode.  
  
 Verwenden Sie zum Aufheben der Registrierung einer Bibliotheks die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Methode.  
  
 Abrufen eines Verweises auf die Objekt-Manager, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, übergeben die <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> -service-ID, `GetService` Methode.  
  
## <a name="registering-and-unregistering-a-library-with-the-object-manager"></a>Registrieren und Aufheben der Registrierung für einer Bibliothek mit der Objekt-Manager  
  
#### <a name="to-register-a-library-with-the-object-manager"></a>Um eine Bibliothek mit der Objekt-Manager zu registrieren.  
  
1. Erstellen Sie eine Bibliothek an.  
  
    ```vb  
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing  
    Private m_nLibraryCookie As UInteger = 0  
    ' Create Library.  
    m_CallBrowserLibrary = New CallBrowser.Library()  
    ```  
  
    ```csharp  
    private CallBrowser.Library m_CallBrowserLibrary = null;  
    private uint m_nLibraryCookie = 0;  
    // Create Library.  
    m_CallBrowserLibrary = new CallBrowser.Library();  
  
    ```  
  
2. Rufen Sie einen Verweis auf ein Objekt der <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> geben, und rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> Methode.  
  
    ```vb  
    Private Sub RegisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            Throw New Exception("Library already registered with Object Manager")  
        End If  
  
        ' Obtain a reference to IVsObjectManager2 type object.  
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
        If objManager Is Nothing Then  
            Throw New NullReferenceException("GetService failed for SVsObjectManager")  
        End If  
  
        Try  
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)  
        Catch e As Exception  
            ' Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message)  
            Throw  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    private void RegisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
            throw new Exception("Library already registered with Object Manager");  
  
        // Obtain a reference to IVsObjectManager2 type object.  
        IVsObjectManager2 objManager =   
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
        if (objManager == null)  
            throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
        try  
        {  
            int hr =   
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,   
                                                 out m_nLibraryCookie);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
        }  
        catch (Exception e)  
        {  
            // Code to handle any CLS-compliant exception.  
            Trace.WriteLine(e.Message);  
            throw;  
        }  
    }  
  
    ```  
  
#### <a name="to-unregister-a-library-with-the-object-manager"></a>Beim Aufheben der Registrierung einer Bibliotheks mit der Objekt-manager  
  
1. Rufen Sie einen Verweis auf ein Objekt der <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> geben, und rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> Methode.  
  
    ```vb  
    Private Sub UnregisterLibrary()  
        If m_nLibraryCookie <> 0 Then  
            ' Obtain a reference to IVsObjectManager2 type object.  
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)  
            If objManager Is Nothing Then  
                Throw New NullReferenceException("GetService failed for SVsObjectManager")  
            End If  
  
            Try  
                objManager.UnregisterLibrary(m_nLibraryCookie)  
            Catch e As Exception  
                ' Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message)  
                Throw  
            Finally  
                m_nLibraryCookie = 0  
            End Try  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UnregisterLibrary()  
    {  
        if (m_nLibraryCookie != 0)  
        {  
            // Obtain a reference to IVsObjectManager2 type object.  
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;  
            if (objManager == null)  
                throw new NullReferenceException("GetService failed for SVsObjectManager");  
  
            try  
            {  
                objManager.UnregisterLibrary(m_nLibraryCookie);  
            }  
            catch (Exception e)  
            {  
                // Code to handle any CLS-compliant exception.  
                Trace.WriteLine(e.Message);  
                throw;  
            }  
            finally  
            {  
                m_nLibraryCookie = 0;  
            }  
        }  
    }  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterbarkeit von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-extensibility.md)   
 [Unterstützung von Tools zum Durchsuchen von Symbolen](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Vorgehensweise: Verfügbarmachen der Listen von Symbolen, die von der Bibliothek bereitgestellt, der Objekt-Manager](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
