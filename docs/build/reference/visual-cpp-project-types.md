---
title: Visual C++-Projekttypen
ms.date: 07/02/2019
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: 98f8ea11cce61ca91fbdc8f8afb900a7ba5b42c9
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552211"
---
# <a name="c-project-templates"></a>C++-Projektvorlagen

Visual Studio-Projektvorlagen generiert Quellcodedateien, Compileroptionen, Menüs, Symbolleisten, Symbole, Verweise und `#include` Anweisungen, die für die Art von Projekt geeignet sind, Sie erstellen möchten. Visual Studio umfasst verschiedene Arten von C++ Projektvorlagen und für viele von ihnen stellt Assistenten bereit, sodass Sie Ihre Projekte anpassen können, erstellen. Sie können die Anwendung unmittelbar nach dem Erstellen eines Projekts erstellen und ausführen. Es ist empfehlenswert, den Buildprozess in Abständen durchzuführen, während Sie Ihre Anwendung entwickeln.

> [!NOTE]
> Mit C++-Projektvorlagen können Sie ein C-Sprachprojekt erstellen. Suchen Sie im generierten Projekt die Dateien mit der Dateinamenerweiterung .cpp, und ändern Sie sie in .c. Erweitern Sie dann auf der Seite **Projekteigenschaften** für das Projekt (nicht für die Projektmappe) die Option **Konfigurationseigenschaften**, **C/C++** , und wählen Sie dann **Erweitert**. Ändern Sie die Einstellung **Kompilierungsart** in **Als C-Code kompilieren (/TC)** .

## <a name="project-templates"></a>Projektvorlagen

Die in Visual Studio enthaltenen Projektvorlagen hängen von der Produktversion und den Workloads ab, die Sie installiert haben. Wenn Sie die Desktop-Entwicklung mit installiert haben C++ Visual Studio-Workload hat diese C++ -Projektvorlagen.

### <a name="windows-desktop"></a>Windows-Desktop

|Projektvorlage|Beschreibung|
|----------------------|-----------------------------|
|[Windows-Konsolenanwendung](../../windows/creating-a-console-application.md)|Ein Projekt zum Erstellen einer Windows-Konsolenanwendung|
|[Windows-Desktopanwendung](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Ein Projekt zum Erstellen einer Windows-Desktopanwendung (Win32)|
|[Dynamic Link Library](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Ein Projekt zum Erstellen einer Dynamic Link Library (DLL)|
|[Statische Bibliothek](../../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Ein Projekt zum Erstellen einer statischen Bibliothek (LIB)|
|Windows-Desktop-Assistenten|Ein Assistent zum Erstellen von Windows-Desktopanwendungen und -Bibliotheken mit zusätzlichen Optionen|

### <a name="general"></a>Allgemein

|Projektvorlage|Beschreibung|
|----------------------|-----------------------------|
|Leeres Projekt|Ein leeres Projekt zum Erstellen einer Anwendung, Bibliothek oder DLL. Sie müssen erforderlichen Code oder Ressourcen hinzufügen.|
|[Makefile-Projekt](creating-a-makefile-project.md)|Ein Projekt, das eine Windows-Makefile in einem Visual Studio-Projekt umschließt. (Öffnen Sie eine Makefile als-ist in Visual Studio verwenden [Ordner öffnen](../open-folder-projects-cpp.md).|
|Projekt mit freigegebenen Elementen|Ein Projekt für die Freigabe von Dateien mit Code oder Ressourcendateien zwischen mehreren Projekten verwendet wird. Dieser Projekttyp wird eine ausführbare Datei nicht erstellt werden.|

### <a name="atl"></a>ATL

|Projektvorlage|Beschreibung|
|----------------------|-----------------------------|
|[ATL-Projekt](../../atl/reference/creating-an-atl-project.md)|Ein Projekt, das die Active Template Library (ATL) verwendet|

### <a name="test"></a>Test

|Projektvorlage|Beschreibung|
|----------------------|-----------------------------|
|[Natives Komponententestprojekt](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Ein Projekt, das native C++-Komponententests enthält|

### <a name="mfc"></a>MFC

Wenn Sie Ihrer Visual Studio-Installation die Komponente für die MFC- und ATL-Unterstützung hinzufügen, werden die folgenden Projektvorlagen in Visual Studio hinzugefügt.

|Projektvorlage|Beschreibung|
|----------------------|-----------------------------|
|[MFC-Anwendung](../../mfc/reference/creating-an-mfc-application.md)|Ein Projekt zum Erstellen einer Anwendung, die die MFC-Bibliothek verwendet.|
|[MFC-ActiveX-Steuerelement](../../mfc/reference/creating-an-mfc-activex-control.md)|Ein Projekt zum Erstellen eines ActiveX-Steuerelements, das die MFC-Bibliothek verwendet.|
|[MFC-DLL](../../mfc/reference/creating-an-mfc-dll-project.md)|Ein Projekt zum Erstellen einer DLL, die die MFC-Bibliothek verwendet.|

### <a name="windows-universal-apps"></a>Universelle Windows-Apps

Wenn Sie Ihrer Visual Studio-Installation die Komponente für C++-Tools für die Universelle Windows Plattform hinzufügen, werden die folgenden Projektvorlagen in Visual Studio hinzugefügt.

Einen Überblick über Universelle Windows-Apps in C++ finden Sie unter [Universal Windows Apps (C++) (Universelle Windows-Apps (C++))](../../cppcx/universal-windows-apps-cpp.md).

|Projektvorlage|Beschreibung|
|----------------------|-----------------------------|
|Leere App|Ein Projekt für eine einseitige UWP-App ohne vordefinierte Steuerelemente oder Layouts.|
|DirectX 11-App|Ein Projekt für eine UWP-App, die DirectX 11 verwendet.|
|DirectX 12-App|Ein Projekt für eine UWP-App, die DirectX 12 verwendet.|
|DirectX 11- und XAML-App|Ein Projekt für eine UWP-App, die DirectX 11 und XAML verwendet.|
|Komponententest-App|Ein Projekt zum Erstellen einer Komponententest-App für UWP-Apps.|
|DLL|Ein Projekt für eine native DLL (Dynamic Link Library), die von einer UWP-App oder Komponente für Windows-Runtime verwendet werden kann.|
|Statische Bibliothek|Ein Projekt für eine native LIB (Static Link Library), die von einer UWP-App oder Komponente für Windows-Runtime verwendet werden kann.|
|Komponente für Windows-Runtime|Ein Projekt für eine Komponente für Windows-Runtime, die von einer UWP-App verwendet werden kann, unabhängig von der Programmiersprache, in der die App geschrieben ist.|
|Paketerstellungsprojekt für Windows-Anwendungen|Ein Projekt, das ein UWP-Paket erstellt, mit dem eine Desktopanwendung über Microsoft Store quer geladen oder verteilt werden kann.|

## <a name="todo-comments"></a>TODO-Kommentare

Viele der mit einer Projektvorlage generierten Dateien enthalten TODO-Kommentare, um Ihnen beim Identifizieren von Orten zu helfen, an denen Sie Ihren eigenen Quellcode bereitstellen können. Weitere Informationen zum Hinzufügen von Code finden Sie unter [Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md) und [Working with Resource Files (Arbeiten mit Ressourcendateien)](../../windows/working-with-resource-files.md).


