---
title: Erweiterte Features, MFC-Anwendungs-Assistent
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: 44d85e7614f6a82af2e58f03a6d65d5d7740ab9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338427"
---
# <a name="advanced-features-mfc-application-wizard"></a>Erweiterte Features, MFC-Anwendungs-Assistent

Unter diesem Thema werden die Optionen für zusätzliche Funktionen für Ihre Anwendung aufgeführt, zum Beispiel eine Hilfefunktion, Druckunterstützung usw. Legen Sie in den einzelnen Abschnitten zusätzliche Unterstützungsoptionen für die erweiterten Funktionen fest.

- **Kontextbezogene Hilfe (HTML)**

   Generiert einen Satz von Hilfedateien für die kontextbezogene Hilfe, verfügbar über F1 und ein Menü "Hilfe" oder durch Klicken auf eine **Hilfe** Schaltfläche in einem Dialogfeld. Zur Unterstützung der Hilfe ist der Hilfecompiler erforderlich. Sie können den Hilfecompiler nachträglich installieren, indem Sie Setup erneut ausführen.

   Finden Sie unter [HTML-Hilfe: Kontextbezogene Hilfe für Programme](../../mfc/html-help-context-sensitive-help-for-your-programs.md) und [Hilfedateien (HTML-Hilfe)](../../build/reference/help-files-html-help.md) für Weitere Informationen.

- **Drucken und Druckvorschau**

   Erstellt den Code zur Behandlung der Druck-, druckeinrichtungs- und seitenansichtsbefehle, indem das Aufrufen von Memberfunktionen in der [CView-Klasse](../../mfc/reference/cview-class.md) der MFC-Bibliothek. Zusätzlich fügt der Assistent dem Anwendungsmenü Befehle für diese Funktionen hinzu. Druckunterstützung steht nur für Anwendungen, die angeben, **Unterstützung für die Dokument-/Ansicht** in die [Anwendungstyp, MFC-Anwendungs-Assistent](../../mfc/reference/application-type-mfc-application-wizard.md) Seite des Assistenten. Dokument-/Ansichtsanwendungen verfügen standardmäßig über Druckunterstützung.

- **Automatisierung**

   Gibt an, dass in der Anwendung Objekte bearbeitet werden können, die in einer anderen Anwendung implementiert wurden, bzw. stellt der Anwendung Automatisierungsclients zur Verfügung.

- **ActiveX-Steuerelemente**

   Unterstützt ActiveX-Steuerelemente (Standard). Wenn Sie nicht mit dieser Option und einem späteren Zeitpunkt ActiveX-Steuerelemente in das Projekt einfügen möchten, müssen Sie einen Aufruf hinzufügen [AfxEnableControlContainer](ole-initialization.md#afxenablecontrolcontainer) in Ihrer Anwendungsverzeichnis [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) Member -Funktion.

- **MAPI (Messaging-API)**

   Gibt an, dass der Benutzer in der Anwendung E-Mail-Nachrichten erstellen, bearbeiten, übertragen und speichern kann.

- **Windows-sockets**

   Unterstützt Windows-Sockets, mit denen Sie Anwendungen schreiben können, die über TCP/IP-Netzwerke kommunizieren.

- **Active Accessibility**

   Bietet Unterstützung für [IAccessible](/windows/desktop/api/oleacc/nn-oleacc-iaccessible) zu [CWnd](../../mfc/reference/cwnd-class.md)-abgeleiteten Klassen, die Sie zum Anpassen der Benutzeroberfläche für eine bessere Interaktion mit barrierefreiheitsclients verwenden können.

- **Allgemeines Steuerelementmanifest**

   Standardmäßig aktiviert. Erstellt ein Anwendungsmanifest zur Aktivierung der im Lieferumfang von Microsoft Windows XP und von neueren Betriebssystemen enthaltenen DLL für allgemeine Steuerelemente.

   Version 6 der DLL für allgemeine Steuerelemente aktualisiert die Vorläuferversion eines allgemeinen Steuerelements, das von einer vorhandenen Anwendung verwendet wird, nicht automatisch. Um die DLL für allgemeine Steuerelemente, Version 6, verwenden zu können, müssen Sie ein Anwendungsmanifest erstellen, das Ihre Anwendung anweist, die neue DLL zu laden. Die DLL für allgemeine Steuerelemente unterstützt auch Windows XP-Designs.

   Durch ein Anwendungsmanifest können auch andere, von Ihrer Anwendung benötigte DLLs und Versionen festgelegt werden. Weitere Informationen zu Anwendungsmanifesten finden Sie unter [isolierte Anwendungen und Seite-an-Seite-Assemblys](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) im Windows SDK.

- **Unterstützung für Neustart-Manager**

   Bietet Unterstützung für die [Windows-Neustart-Manager](/windows/desktop/RstMgr/using-restart-manager). In diesem Video zeigt, wie Sie den Neustart-Manager von MFC verwendet wird: [Gewusst wie: Verwenden des neuen Neustart-Managers](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100)).

- **Erweiterte Framebereiche**

   |Option|Beschreibung|
   |------------|-----------------|
   |**Andockbarer Explorer-Bereich**|Erstellt einen andockbaren Bereich, die Visual Studio ähnelt **Projektmappen-Explorer** links vom Hauptrahmenfenster.|
   |**Andockbarer Ausgabebereich**|Erstellt einen andockbaren Bereich, die Visual Studio ähnelt **Ausgabe** Bereich, der sich das Hauptrahmenfenster befindet.|
   |**Andockbarer Eigenschaftenbereich**|Erstellt einen andockbaren Bereich, die Visual Studio ähnelt **Eigenschaften** Bereich rechts vom Hauptrahmenfenster.|
   |**Navigationsbereich**|Erstellt einen andockbaren Bereich, der der Outlook-Navigationsleiste links vom Hauptrahmenfenster ähnelt.|
   |**Titelleiste**|Erstellt eine Titelleiste im Office-Stil über dem Hauptrahmenfenster.|

- **Anzahl an Dateien in der Liste zuletzt geöffneter Dateien**

   Gibt die Anzahl der Dateien an, die in der Liste der zuletzt verwendeten Dateien angezeigt werden soll. Die Anzahl beträgt standardmäßig 4.

## <a name="see-also"></a>Siehe auch

[MFC-Anwendungs-Assistent](../../mfc/reference/mfc-application-wizard.md)
