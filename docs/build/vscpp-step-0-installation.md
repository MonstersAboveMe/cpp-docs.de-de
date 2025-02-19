---
title: Installieren der C++-Unterstützung in Visual Studio
description: Installieren Sie Visual Studio-Unterstützung für Visual C++
ms.custom: mvc
ms.date: 04/02/2019
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d70-719d-42dc-90d7-1d0ca31a2f54
ms.openlocfilehash: 2c2bed4063194bdc3c0f3fbc405be6bf9a4031e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315146"
---
# <a name="install-c-support-in-visual-studio"></a>Installieren der C++-Unterstützung in Visual Studio

Wenn Sie noch nicht heruntergeladen und Visual Studio und Visual C++-Tools noch nicht installiert, sieht aus wie für den Einstieg.

::: moniker range="vs-2019"

## <a name="visual-studio-2019-installation"></a>Visual Studio-Installation 2019

Willkommen bei Visual Studio 2019. In dieser Version können Sie ganz einfach die Features auswählen und installieren, die Sie benötigen. Und aufgrund des reduzierten minimalen Speicherbedarfs, werden sie schnell und mit weniger Beeinträchtigung des Systems installiert.

> [!NOTE]
> Dieses Thema gilt für die Installation von Visual Studio unter Windows. [Visual Studio Code](https://code.visualstudio.com/) ist eine einfache, plattformübergreifende Entwicklungsumgebung, die auf Windows, Mac und Linux-Systemen ausgeführt wird. Microsoft [C-/C++ für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools) -Erweiterung unterstützt IntelliSense, debugging, codeformatierung, automatische Vervollständigung. Visual Studio für Mac nicht Microsoft C++ unterstützt, unterstützt jedoch .NET-Sprachen und plattformübergreifende Entwicklung. Installationsanweisungen finden Sie unter [Installieren von Visual Studio für Mac](/visualstudio/mac/installation/).

Sie möchten mehr zu weiteren Neuerungen in dieser Version wissen? Finden Sie unter der Visual Studio [Anmerkungen zu dieser Version](/visualstudio/releases/2019/release-notes/).

Bereit für die Installation? Schauen Sie sich diese Schritt-für-Schritt Anleitung an.

### <a name="step-1---make-sure-your-computer-is-ready-for-visual-studio"></a>Schritt 1: Stellen Sie sicher, dass Ihr Computer für Visual Studio bereit ist

Vor der Installation von Visual Studio:

1. Informieren Sie sich über die [Systemanforderungen](/visualstudio/releases/2019/system-requirements). Anhand dieser Anforderungen können Sie feststellen, ob Ihr Computer Visual Studio 2019 unterstützt.

1. Laden Sie die aktuellen Windows-Updates herunter. So stellen Sie sicher, dass Ihr Computer sowohl die neuesten Sicherheitsupdates als auch die erforderlichen Systemkomponenten für Visual Studio hat.

1. Starten Sie den Computer neu. Dadurch wird sichergestellt, dass keine ausstehenden Installationen oder Updates die Installation von Visual Studio behindern.

1. Geben Sie Speicherplatz frei. Entfernen Sie nicht benötigte Dateien und Anwendungen z.B. mit der Datenträgerbereinigung-App von Ihrem %Systemlaufwerk%.

Informationen zur parallelen Ausführung vorheriger Versionen von Visual Studio und Visual Studio 2019 finden Sie auf der Seite [Visual Studio 2019 – Zielplattformen und Kompatibilität](/visualstudio/releases/2019/compatibility/).

### <a name="step-2---download-visual-studio"></a>Schritt 2: Herunterladen von Visual Studio

Laden Sie danach die Visual Studio-Bootstrapperdatei herunter. Klicken Sie zu diesem Zweck auf die folgende Schaltfläche, wählen Sie die gewünschte Edition von Visual Studio aus, und klicken Sie dann auf **Speichern** und **Ordner öffnen**.

 > [!div class="button"]
 > [Herunterladen von Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019+rc)

### <a name="step-3---install-the-visual-studio-installer"></a>Schritt 3: Installieren des Visual Studio-Installers

Führen Sie die Bootstrapperdatei aus, um den Visual Studio-Installer zu installieren. Dieses neue, schlanke Installationsprogramm enthält alle Elemente, die Sie zum Installieren und Anpassen von Visual Studio benötigen.

1. Doppelklicken Sie in Ihrem Ordner **Downloads** auf die Bootstrapperdatei, die einer der folgenden Dateien entspricht oder ähnelt:

   * **vs_community.exe** für Visual Studio Community
   * **vs_professional.exe** für Visual Studio Professional
   * **vs_enterprise.exe** für Visual Studio Enterprise

   Wenn eine Benachrichtigung der Benutzerkontensteuerung angezeigt wird, klicken Sie auf **Ja**.

1. Sie werden gebeten, die Microsoft-[Lizenzbedingungen](https://visualstudio.microsoft.com/license-terms/) und die Microsoft-[Datenschutzbestimmungen](https://privacy.microsoft.com/privacystatement) zu akzeptieren. Klicken Sie auf **Weiter**.

### <a name="step-4---choose-workloads"></a>Schritt 4: Auswählen von Workloads

Nachdem das Installationsprogramm installiert ist, können Sie sie zum Anpassen Ihrer Installation durch Auswahl der *Workloads*, oder ein feature von Mengen, die Sie möchten. Gehen Sie folgendermaßen vor:

1. Suchen Sie die gewünschten Arbeitsauslastungen im Bildschirm **Visual Studio wird installiert**.

   ![Visual Studio 2019: Workload installieren](../get-started/media/vs-installer-workloads.png)

   Wählen Sie für C++-Core-Unterstützung die Workload "Desktopentwicklung mit C++" aus. Sie wird mit dem standardmäßigen Kern-Editor bereitgestellt, der die grundlegende Codebearbeitung für über 20 Sprachen, die Möglichkeit, Code aus einem beliebigen Ordner heraus zu öffnen und zu bearbeiten, ohne dass ein Projekt erforderlich ist, und die integrierte Quellcodekontrolle unterstützt.

   Zusätzlicher Workloads unterstützt andere Arten von C++-Entwicklung. Wählen Sie z. B. die "Universelle Windows-Plattform-Entwicklung"-arbeitsauslastung zum Erstellen von apps, die die Windows-Runtime für den Microsoft Store verwenden. Wählen Sie "Spieleentwicklung mit C++" zum Erstellen von Spielen, die DirectX, Unreal und Cocos2d verwenden. Wählen Sie "Linux-Entwicklung mit C++", Ziel-Linux-Plattformen, einschließlich der IoT-Entwicklung.

   Die **Installationsdetails** Bereich zeigt enthalten und optionalen Komponenten installiert, indem Sie jede Workload. Sie können aktivieren oder deaktivieren die optionale Komponenten in dieser Liste. Wählen Sie z. B. um Entwicklung mithilfe der Visual Studio 2017 oder 2015-Compiler-Toolsets zu unterstützen, die MSVC v141 oder MSVC v140 optionalen Komponenten. Sie können Unterstützung für MFC, die experimentellen Module-spracherweiterung, IncrediBuild und weitere hinzufügen.

1. Wählen Sie nach der Auswahl der arbeitsauslastungen und optionalen Komponenten, die gewünschten **installieren**.

    Als Nächstes werden Statusbildschirme angezeigt, die über den Fortschritt der Installation von Visual Studio informieren.

> [!TIP]
> Nach der Installation können Sie jederzeit die Installation von Workloads oder Komponenten nachholen. Wenn Sie Visual Studio geöffnet haben, navigieren Sie zu **Extras** > **Tools und Features abrufen…**. Dadurch wird der Visual Studio-Installer geöffnet. Öffnen Sie den **Visual Studio-Installer** alternativ über das Startmenü. Nun können Sie die Workloads oder Komponenten auswählen, die Sie installieren möchten. Klicken Sie anschließend auf **Ändern**.

## <a name="step-5---choose-individual-components-optional"></a>Schritt 5: Auswählen einzelner Komponenten (optional)

Wenn Sie nicht das Feature für Workloads verwenden möchten, um Ihre Visual Studio-Installation anzupassen, oder Sie mehr Komponenten hinzufügen möchten, als von einer Workload installiert werden, können Sie individuelle Komponenten über die Registerkarte **Einzelne Komponenten** installieren bzw. hinzufügen. Wählen Sie die gewünschten Komponenten aus, und führen Sie dann die Anweisungen aus.

  ![Visual Studio 2019: Installieren einzelner Komponenten](../get-started/media/vs-installer-individual-components.png "Installieren einzelner Visual Studio-Komponenten")

## <a name="step-6---install-language-packs-optional"></a>Schritt 6: Installieren von Language Packs (optional)

Standardmäßig versucht das Installationsprogramm bei der ersten Ausführung die Sprache des Betriebssystems zu verwenden. Zum Installieren von Visual Studio in einer Sprache Ihrer Wahl klicken Sie im Visual Studio-Installer auf die Registerkarte **Sprachpakete**, und folgen Sie dann den Anweisungen.

  ![Visual Studio 2019 – Installieren von Sprachpaketen](../get-started/media/vs-installer-language-packs.png "Installieren von Visual Studio-Sprachpaketen")

### <a name="change-the-installer-language-from-the-command-line"></a>Ändern der Installersprache über die Befehlszeile

Eine andere Möglichkeit zum Ändern der Standardsprache ist die Ausführung des Installers über die Befehlszeile. Mit dem Befehl `vs_installer.exe --locale en-US` können Sie z.B. erzwingen, dass das Installationsprogramm auf Englisch ausgeführt wird. Das Installationsprogramm speichert diese Einstellung aus, wenn er das nächste Mal ausgeführt wird. Der Installer unterstützt die folgenden Sprachtoken: zh-CN, zh-TW, cs-CZ, en-US, es-ES, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU und tr-TR.

### <a name="step-7---change-the-installation-location-optional"></a>Schritt 7: Ändern des Installationspfads (optional)

Sie können den Speicherbedarf für die Installation von Visual Studio auf Ihrem Systemlaufwerk reduzieren. Sie können den Downloadcache, freigegebene Komponenten, SDKs und Tools auf andere Datenträger verschieben, und Visual Studio dort belassen, wo es am schnellsten ausgeführt werden kann.

  ![Visual Studio 2019: Ändern des Installationspfads](../get-started/media/vs-installer-installation-locations.png "Ändern des Installationspfads")

> [!IMPORTANT]
> Sie können nur bei der ersten Installation von Visual Studio ein anderes Laufwerk auswählen. Wenn Sie Visual Studio bereits installiert haben und das Laufwerk wechseln möchten, müssen Sie Visual Studio deinstallieren und anschließend neu installieren.

## <a name="step-8---start-developing"></a>Schritt 8: Mit dem Entwickeln beginnen

1. Klicken Sie nach Abschluss der Visual Studio-Installation auf **Starten**, um mit dem Programmieren in Visual Studio zu beginnen.

1. Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

1. Geben Sie den Typ von App im Suchfeld ein, den Sie erstellen möchten, um eine Liste der verfügbaren Vorlagen anzuzeigen. Die Liste der Vorlagen basiert auf den Workloads, die Sie bei der Installation ausgewählt haben. Wählen Sie andere Workloads aus, um andere Vorlagen anzuzeigen.

   Sie können die Suchergebnisse nach bestimmten Programmiersprachen filtern, indem Sie die Dropdownliste **Sprache** verwenden. Sie können außerdem die Listen **Plattform** und **Projekttyp** zum Filtern verwenden.

1. Ihr neues Projekt wird dann in Visual Studio geöffnet, und Sie können damit anfangen, Code zu schreiben.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="visual-studio-2017-installation"></a>Visual Studio 2017-Installation

In Visual Studio 2017 ist es einfach auswählen und installieren nur die benötigten Funktionen. Und aufgrund des reduzierten minimalen Speicherbedarfs, werden sie schnell und mit weniger Beeinträchtigung des Systems installiert.

### <a name="prerequisites"></a>Vorraussetzungen

- Eine Breitband-Internetverbindung. Visual Studio-Installer kann mehrere Gigabyte Daten herunterladen.

- Ein Computer, der Microsoft Windows 7 oder höher ausgeführt wird. Wir empfehlen die Windows 10, für die bestmögliche entwicklungserfahrung. Stellen Sie sicher, dass die neuesten Updates für Ihr System angewendet werden, vor der Installation von Visual Studio.

- Ausreichend freier Speicherplatz auf dem Datenträger. Visual Studio erfordert mindestens 7 GB Speicherplatz und dauert mindestens 50 GB, wenn viele allgemeine Optionen installiert sind. Es wird empfohlen, dass Sie es auf Ihrem Laufwerk "c:" installieren.

Weitere Informationen zu den freien Speicherplatz und den Anforderungen des Betriebssystems, finden Sie unter [Visual Studio Systemanforderungen der Produktfamilie](/visualstudio/productinfo/vs2017-system-requirements-vs). Das Installationsprogramm gibt an, wie viel Speicherplatz für die Optionen erforderlich ist, die Sie auswählen.

### <a name="download-and-install"></a>Herunterladen und installieren

1. Laden Sie das neueste Visual Studio 2017-Installationsprogramm für Windows herunter.

   > [!div class="nextstepaction"]
   > [Installieren von Visual Studio 2017 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)

   >[!Tip]
   > Die Community Edition eignet sich für einzelne Entwickler, Schulungsumgebungen, akademische Forschung und Open Source-Entwicklung. Installieren Sie für andere Verwendungen [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) oder [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

1. Suchen Sie die Installer-Datei, die Sie heruntergeladen haben und ihn ausführen. Sie können in Ihrem Browser angezeigt werden, oder Umständen ist es in Ihrem Ordner "Downloads". Das Installationsprogramm benötigt Administratorrechte ausgeführt. Sie sehen möglicherweise eine **User Account Control** Dialogfeld werden Sie aufgefordert, erteilen Sie Berechtigungen zum können des Installationsprogramms, nehmen Sie Änderungen an Ihrem System aus, wählen **Ja**. Wenn Sie Probleme haben, suchen Sie die heruntergeladene Datei im Datei-Explorer, mit der rechten Maustaste auf das Symbol "Installer" aus, und wählen **als Administrator ausführen** aus dem Kontextmenü.

   ![Herunterladen und installieren Sie Visual Studio-Installer](media/vscpp-concierge-run-installer.gif "herunterladen und installieren Sie Visual Studio-Installer")

1. Der Installer bietet Ihnen eine Liste von Workloads, bei denen es sich um Gruppen von verwandten Optionen für bestimmte Entwicklungsbereiche handelt. Unterstützung für C++ ist jetzt Teil der optionalen Workloads, die standardmäßig installiert sind.

   ![Desktopentwicklung mit C++-Arbeitslast](media/desktop-development-with-cpp.png "Desktopentwicklung mit C++")

   Wählen Sie für C++, die **Desktopentwicklung mit C++** Workload und wählen Sie dann **installieren**.

   ![Installieren Sie die Desktopentwicklung mit C++-Arbeitslast](media/vscpp-concierge-choose-workload.gif "installieren Sie die Desktopentwicklung mit C++-Arbeitslast")

1. Wählen Sie nach Abschluss der Installation der **starten** Schaltfläche zum Starten von Visual Studio.

   Beim ersten Ausführen von Visual Studio werden Sie aufgefordert, sich mit einem Microsoft Account anmelden. Wenn Sie über keins verfügen, können Sie es kostenloses erstellen. Sie müssen auch ein Design auswählen. Keine Sorge, Sie können ihn später ändern, wenn Sie möchten.

   Es dauert Visual Studio mehrere Minuten auf vorzubereiten verwenden den ersten, die sie ausführen. So sieht es wie in der eine schnelle, die mit:

   ![Melden Sie sich bei Visual Studio 2017](media/vscpp-quickstart-first-run.gif "melden Sie sich bei Visual Studio 2017")

   Visual Studio startet viel schneller, wenn Sie es erneut ausführen.

1. Wenn Visual Studio geöffnet wird, überprüfen Sie, wenn markiert ist, dass Sie das Symbol in der Titelleiste an:

   ![Visual Studio 2017-Benachrichtigungskennzeichen](media/vscpp-first-start-page-flag.png "Benachrichtigungshinweis für Visual Studio 2017")

   Wenn er hervorgehoben wird, wählen Sie diese zum Öffnen der **Benachrichtigungen** Fenster. Wenn keine Updates für Visual Studio verfügbar sind, empfehlen wir, dass Sie dies jetzt tun. Sobald die Installation abgeschlossen ist, starten Sie Visual Studio neu.

::: moniker-end

::: moniker range="<vs-2017"

## <a name="visual-studio-2015-installation"></a>Visual Studio 2015-Installation

Auf der Seite [Downloads älterer Versionen von Visual Studio](https://www.visualstudio.com/vs/older-downloads/) können Sie Visual Studio 2015 herunterladen. Führen Sie das Setupprogramm aus, klicken Sie auf **Benutzerdefinierte Installation**, und wählen Sie die C++-Komponente aus. Um eine vorhandene Installation von Visual Studio 2015 C++-Unterstützung hinzuzufügen, klicken Sie auf die Schaltfläche "Windows Start", und geben auf **Software**. Öffnen Sie das Programm in der Ergebnisliste aus, und klicken Sie dann finden Sie die Installation von Visual Studio 2015 in der Liste der installierten Programme. Doppelklicken Sie darauf, und wählen Sie dann **ändern** , und wählen Sie die Visual C++, die zu installierenden Komponenten.

In der Regel wird die Verwendung von Visual Studio 2017 empfohlen, auch wenn Sie dann Ihren Code mithilfe des Visual Studio 2015-Compilers kompilieren müssen. Weitere Informationen finden Sie unter [Use native multi-targeting in Visual Studio to build old projects (Verwenden der nativen Festlegung von Zielversionen in Visual Studio, um alte Projekte zu erstellen)](../porting/use-native-multi-targeting.md).

::: moniker-end

Wenn Visual Studio ausgeführt wird, können Sie mit dem nächsten Schritt fortfahren.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen Sie ein C++-Projekt](vscpp-step-1-create.md)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
