---
title: Erstellen eines C++-Makefile-Projekts in Visual Studio
ms.date: 05/16/2019
f1_keywords:
- vc.appwiz.makefile.project
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
ms.openlocfilehash: b460b16b3a64818501187b00e503ad0179d26443
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837392"
---
# <a name="create-a-c-makefile-project"></a>Erstellen eines C++-Makefile-Projekts

Ein *Makefile* ist eine Textdatei, die Anweisungen zum Kompilieren und Linken (oder *Erstellen*) einer Reihe von C++-Quellcodedateien enthält. Ein *Make*-Programm liest das Makefile und ruft einen Compiler, einen Linker und möglicherweise auch andere Programme auf, um eine ausführbare Datei zu erstellen. Die Implementierung des Programms *make* von Microsoft trägt den Namen [NMAKE](nmake-reference.md);

Wenn Sie über ein vorhandenes Makefile-Projekt verfügen, können Sie folgende Optionen auswählen, wenn Sie es in der Visual Studio-IDE codieren und/oder debuggen möchten:

- Erstellen eines Makefile-Projekts in Visual Studio, das Ihr vorhandenes Makefile verwendet, um eine VCXPROJ-Datei zu konfigurieren, die von Visual Studio für IntelliSense verwendet wird. (Sie verfügen nicht über alle IDE-Funktionen, die Sie mit einem nativen MSBuild-Projekt erhalten.) Siehe [So erstellen Sie ein Makefile-Projekt](#create_a_makefile_project) weiter unten.
- Verwenden des Assistenten für das **Erstellen von Projekten aus vorhandenen Codedateien**, um ein natives MSBuild-Projekt aus dem Quellcode zu erstellen. Das ursprüngliche Makefile wird nach diesem Vorgang nicht verwendet. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines C++-Projekts aus vorhandenem Code](../how-to-create-a-cpp-project-from-existing-code.md).
- **Visual Studio 2017 und höher:** Verwenden Sie die Funktion **Ordner öffnen**, um ein Makefile-Projekt zu bearbeiten und in der vorliegenden Form zu erstellen, ohne Beteiligung des MSBuild-Systems. Weitere Informationen finden Sie unter [Open Folder projects for C++ (Verwenden von „Ordner öffnen“ mit Projekten in Visual C++)](../open-folder-projects-cpp.md).
- **Visual Studio 2019 und höher**: Erstellen eines UNIX-Makefile-Projekts für Linux.

## <a name="a-namecreateamakefileproject-to-create-a-makefile-project-with-the-makefile-project-template"></a><a name="create_a_makefile_project"> So erstellen Sie ein Makefile-Projekt mit der Makefile-Projektvorlage

In Visual Studio 2017 oder höher ist die Makefile-Projektvorlage verfügbar, wenn die Workload C++-Desktopentwicklung installiert ist.

Folgen Sie dem Assistenten, der Sie beim Festlegen der Befehle und der Umgebung unterstützt, die das Makefile verwendet. Anschließend können Sie dieses Projekt verwenden, um Ihren Code in Visual Studio zu erstellen.

Das Makefile-Projekt zeigt im Projektmappen-Explorer standardmäßig keine Dateien an. Die Buildeinstellungen, die auf der Eigenschaftenseite des Projekts angezeigt werden, werden vom Makefile-Projekt festgelegt.

Die Ausgabedatei, die Sie im Projekt festlegen, hat keinen Einfluss auf den vom Buildskript erstellten Namen; sie deklariert lediglich die Bestimmung. Ihr Makefile steuert weiterhin den Buildprozess und gibt die Buildziele an.

::: moniker range="vs-2019"

### <a name="to-create-a-makefile-project-in-visual-studio-2019"></a>So erstellen Sie ein Makefile-Projekt in Visual Studio 2019

1. Wählen Sie im Visual Studio-Hauptmenü **Datei** > **Neu** > **Projekt** aus, und geben Sie im Suchfeld „makefile“ ein. Oder erweitern Sie im Dialogfeld **Neues Projekt** **Visual C++** > **Allgemein** (Visual Studio 2015) oder **Sonstige** (Visual Studio 2017), und wählen Sie dann zwischen den zwei Optionen, je nachdem, ob Windows oder Linux Ihr Ziel darstellt.

1. **Nur Windows**: Geben Sie auf der Seite **Debugkonfigurationseinstellungen** die Befehls-, Ausgabe-, Bereinigungs- und Neuerstellungsinformationen für die Debug- und Verkaufsversion an. Klicken Sie auf **Weiter**, wenn Sie für eine Verkaufskonfiguration abweichende Einstellungen festlegen möchten.

1. Klicken Sie auf **Fertig stellen**, um das Dialogfeld zu schließen und das neu erstellte Projekt im **Projektmappen-Explorer** zu öffnen.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-makefile-project-in-visual-studio-2015-or-visual-studio-2017"></a>So erstellen Sie ein Makefile-Projekt in Visual Studio 2015 oder Visual Studio 2017

1. Geben Sie auf der Visual Studio-Startseite „makefile“ in das Suchfeld **Neues Projekt** ein. Sie können auch **Visual C++** > **Allgemein** (Visual Studio 2015) oder **Andere** (Visual Studio 2017) im Dialogfeld **Neues Projekt** erweitern und dann im Vorlagenbereich auf **Makefile-Projekt** klicken, um den Projekt-Assistenten zu öffnen.

1. Geben Sie auf der Seite **Anwendungseinstellungen** die Befehls-, Ausgabe-, Bereinigungs- und Neuerstellungsinformationen für die Debug- und Verkaufsversion an.

1. Klicken Sie auf **Fertig stellen**, um den Assistenten zu schließen und das neu erstellte Projekt im **Projektmappen-Explorer** zu öffnen.

::: moniker-end

Sie können die Projekteigenschaften auf der Eigenschaftenseite des Projekts anzeigen und bearbeiten. Informationen zum Anzeigen der Eigenschaftenseite finden Sie unter [Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](../working-with-project-properties.md).

## <a name="makefile-project-wizard"></a>Makefile-Projekt-Assistent

Nachdem Sie ein Makefile-Projekt erstellt haben, können Sie die folgenden Optionen auf der **Nmake**-Seite der Eigenschaftenseite Ihres Projekts anzeigen und bearbeiten.

- **Buildbefehlszeile:** Gibt die auszuführende Befehlszeile an, wenn der Benutzer im Menü „Build“ auf „Erstellen“ klickt. Wird im Feld „Buildbefehlszeile“ auf der Seite „Nmake“ der Eigenschaftenseite des Projekts angezeigt.

- **Ausgabe:** Gibt den Namen der Datei an, in der die Ausgabe für die Befehlszeile enthalten ist. Diese Option basiert standardmäßig auf dem Projektnamen. Wird im Feld „Ausgabe“ auf der Seite „Nmake“ der Eigenschaftenseite des Projekts angezeigt.

- **„Bereinigen“-Befehle**: Gibt die auszuführende Befehlszeile an, wenn der Benutzer im Menü „Build“ auf „Bereinigen“ klickt. Wird im Befehlszeilenfeld „Bereinigen“ auf der Seite „Nmake“ der Eigenschaftenseite des Projekts angezeigt.

- **Neuerstellungsbefehlszeile:** Gibt die Befehlszeile an, die ausgeführt werden soll, wenn der Benutzer im Menü „Build“ auf „Neu erstellen“ klickt. Wird im Befehlszeilenfeld „Alles neu erstellen“ auf der Seite „Nmake“ der Eigenschaftenseite des Projekts angezeigt.

## <a name="how-to-enable-intellisense-for-makefile-projects"></a>Vorgehensweise: Aktivieren von IntelliSense für Makefile-Projekte

IntelliSense wird in Makefile-Projekten nicht ordnungsgemäß ausgeführt, wenn bestimmte Projekteinstellungen oder Compileroptionen nicht ordnungsgemäß eingerichtet sind. Führen Sie die folgenden Schritte aus, um Makefileprojekte so zu konfigurieren, dass IntelliSense erwartungsgemäß arbeitet:

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten**. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Erweitern Sie den Knoten **Konfigurationseigenschaften**.

1. Wählen Sie die Eigenschaftenseite **NMake** aus, und ändern Sie dann die Eigenschaften unter **IntelliSense** nach Bedarf.

   - Legen Sie die Eigenschaft **Präprozessordefinitionen** so fest, dass alle Präprozessorsymbole in Ihrem Makefile-Projekt definiert werden. Weitere Informationen finden Sie unter [/D (Preprocessor Definitions) (/D (Präprozessordefinitionen))](d-preprocessor-definitions.md).

   - Legen Sie die Eigenschaft **Includesuchpfad** so fest, dass die Liste von Verzeichnissen angegeben wird, in denen der Compiler sucht, um Dateiverweise aufzulösen, die an Präprozessordirektiven in Ihrem Makefile-Projekt übergeben werden. Weitere Informationen finden Sie unter [/I (Additional Include Directories) (/I (Zusätzliche Includeverzeichnisse))](i-additional-include-directories.md).

    - Legen Sie die Umgebungsvariable **INCLUDE** für Projekte fest, die mithilfe der „cl.exe“ über ein Befehlsfenster erstellt werden, um Verzeichnisse anzugeben, in denen der Compiler sucht, um Dateiverweise aufzulösen, die an Präprozessordirektiven in Ihrem Makefile-Projekt übergeben werden.

   - Legen Sie die Eigenschaft **Erzwungene Includedateien** fest, um anzugeben, welche Headerdateien bei der Erstellung des Makefile-Projekts verarbeitet werden sollen. Weitere Informationen finden Sie unter [/FI (Name Forced Include File) (/FI (Name der expliziten Includedatei))](fi-name-forced-include-file.md).

   - Legen Sie die Eigenschaft **Assemblysuchpfad** fest, um die Liste von Verzeichnissen anzugeben, in denen der Compiler sucht, um Verweise auf .NET-Assemblys in Ihrem Projekt aufzulösen. Weitere Informationen finden Sie unter [/AI (Specify Metadata Directories) (/AI (Metadatenverzeichnisse festlegen))](ai-specify-metadata-directories.md).

   - Legen Sie die Eigenschaft **Erzwungene Verwendung von Assemblys** fest, um anzugeben, welche .NET-Assemblys bei der Erstellung des Makefile-Projekts verarbeitet werden sollen. Weitere Informationen finden Sie unter [/FU (Name Forced #using File) (/FU (Name der erzwungenen #using-Datei))](fu-name-forced-hash-using-file.md).

   - Legen Sie die Eigenschaft **Zusätzliche Optionen** fest, um zusätzliche Compileroptionen anzugeben, die von IntelliSense beim Analysieren von C++-Dateien verwendet werden.

1. Klicken Sie auf **OK**, um die Eigenschaftenseiten zu schließen.

1. Verwenden Sie den Befehl **Alle speichern**, um die geänderten Projekteinstellungen zu speichern.

Führen Sie das nächste Mal, wenn Sie Ihr Makefile-Projekt in der Visual Studio-Entwicklungsumgebung öffnen, den Befehl **Projektmappe bereinigen** und anschließend **Projektmappe erstellen** im Makefile-Projekt aus. IntelliSense sollte nun ordnungsgemäß in der IDE funktionieren.

## <a name="see-also"></a>Siehe auch

[Verwenden von IntelliSense](/visualstudio/ide/using-intellisense)<br>
[NMAKE-Referenz](nmake-reference.md)<br>
[Vorgehensweise: Erstellen eines C++-Projekts aus vorhandenem Code](../how-to-create-a-cpp-project-from-existing-code.md)
[Sonderzeichen in einem Makefile](special-characters-in-a-makefile.md)<br/>
[Inhalt eines Makefiles](contents-of-a-makefile.md)<br/>
