---
title: Übersicht über Windows-Programmierung in C++
ms.date: 07/02/2019
ms.assetid: efc691d7-21f3-47ae-ae56-cab999ccf59d
ms.openlocfilehash: 1f49c9f8f78f83d6ae991b7427b28f7f5cbf7f0c
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552308"
---
# <a name="overview-of-windows-programming-in-c"></a>Übersicht über Windows-Programmierung in C++

Es gibt mehrere allgemeine Kategorien von Windows-Anwendungen, die Sie mit C++ erstellen können. Jede verfügt über eine eigene Programmiermodell und eine Reihe von Windows-spezifischen Bibliotheken, aber die C++ standard-Bibliothek und Drittanbieter- C++ Bibliotheken in einer von ihnen verwendet werden können.

## <a name="command-line-console-applications"></a>Über die Befehlszeile (Konsole)-Anwendungen

C++-konsolenanwendungen, über die Befehlszeile in einem Konsolenfenster ausführen und nur die Ausgabe von Text anzeigen. Weitere Informationen finden Sie unter [Konsolenanwendungen](console-applications-in-visual-cpp.md).

## <a name="native-desktop-client-applications"></a>Systemeigene desktop-Clientanwendungen

Ein *systemeigene desktop-Clientanwendung* ist eine C oder C++ im Fenstermodus-Anwendung, die ursprüngliche systemeigene verwendet [C-Windows-APIs oder APIs von Component Object Model (COM)](/windows/desktop/apiindex/windows-api-list) auf das Betriebssystem. Diese APIs sind sich größtenteils in c geschriebenen Es ist mehr als eine Möglichkeit, eine systemeigene desktop-app zu erstellen: Sie können mithilfe einer Schleife der C-Stil-Nachricht, die Betriebssystemereignisse verarbeitet Programmieren der Win32-APIs direkt verwenden. Alternativ können Sie programmieren, verwenden *Microsoft Foundation Classes* (MFC), eine leichte objektorientierten C++ -Bibliothek, die dient als Wrapper für Win32. Weder Ansatz gilt "modernen" im Vergleich zu den universellen Windows-Plattform (UWP), aber beide werden weiterhin vollständig unterstützt und Millionen von Codezeilen, die derzeit in der Welt ausführen müssen. Eine Win32-Anwendung in einem Fenster verlangt vom Entwickler explizit mit Windows-Nachrichten innerhalb einer Prozedur-Funktion von Windows zu arbeiten. Trotz des Namens kann eine Win32-Anwendung als eine (x86) 32-Bit oder 64-Bit-(x64) binäre kompiliert werden. In der Visual Studio-IDE sind die Begriffe X86 und die Win32-Synonym.

Um den ersten Schritten mit herkömmlichen Windows C++-Programmierung finden Sie unter [erste Schritte mit Win32- und C++](/windows/desktop/LearnWin32/learn-to-program-for-windows). Nachdem Sie ein Verständnis für Win32 erhalten, ist dies einfacher Informationen [MFC-Desktopanwendungen](../mfc/mfc-desktop-applications.md). Ein Beispiel für eine herkömmliche C++-Desktopanwendung, die komplexe Grafiken verwendet, finden Sie unter [Hilo: Entwickeln von C++-Anwendungen für Windows](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx).

### <a name="c-or-net"></a>C++ oder .NET?

In der allgemeinen .NET-Programmierung in C# ist weniger komplex und weniger fehleranfällig und verfügt über eine modernere, objektorientierte API als Win32 oder MFC. In den meisten Fällen ist die Leistung mehr als ausreichend. Der Windows Presentation Foundation (WPF) für komplexe Grafiken für .NET features, und Sie können Win32- und der moderne Windows-Runtime-API nutzen. Es wird empfohlen, als in der Regel mithilfe C++ für desktop-Anwendungen, wenn erforderlich ist:

- präzise Steuerung der speicherauslastung
- der Energieverbrauch soweit wie möglich zu optimieren
- Nutzung der GPU für allgemeine Berechnungen
- der Zugriff auf DirectX
- einer hohen Auslastung der Standard-c++-Bibliotheken

Es ist auch möglich, kombinieren die Leistungsfähigkeit und die Effizienz von C++ mit der Programmierung mit .NET. Sie können eine Benutzeroberfläche in erstellen C# und c++ / CLI, um die Anwendung native C++-Bibliotheken verwenden kann. Weitere Informationen finden Sie unter [.NET-Programmierung mit C++ / CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

## <a name="com-components"></a>COM-Komponenten

Die [Component Object Model (COM)](/windows/desktop/com/the-component-object-model) ist eine Spezifikation, die in verschiedenen Sprachen für die Kommunikation mit anderen geschriebene Programme ermöglicht. Viele Windows-Komponenten werden als COM-Objekte implementiert, und führen Sie die standard-COM-Regeln für die objekterstellung-Schnittstellenermittlung und Zerstörung von Objekten.  COM-Objekte aus der C++-desktop-Anwendungen ist relativ unkompliziert, aber Ihre eigenen COM-Objekt zu schreiben ist komplexer. Die [Active Template Library (ATL)](../atl/atl-com-desktop-components.md) enthält Makros und Hilfsfunktionen, die COM-Entwicklung zu vereinfachen. Weitere Informationen finden Sie unter [ATL-COM-desktop-Komponenten](../atl/atl-com-desktop-components.md).

## <a name="universal-windows-platform-apps"></a>Universelle Windows-Plattform-Apps

Die universelle Windows-Plattform (UWP) ist die moderne Windows-API. UWP-apps auf allen Windows 10-Geräten ausgeführt, verwenden XAML für die Benutzeroberfläche und sind vollständig Touch-fähig. Weitere Informationen zu UWP finden Sie unter [was einer app für die universelle Windows-Plattform (UWP) ist?](/windows/uwp/get-started/whats-a-uwp) und [Anleitung für universelle Windows-Apps](/windows/uwp/get-started/universal-application-platform-guide).

Die ursprüngliche C++ Unterstützung für UWP (1) umfasste C++/CX, ein Dialekt von C++ mit Erweiterungen für die Syntax oder (2) der Windows-Runtime-Bibliothek (WRL), basiert die Standard C++ und COM. Sowohl C + c++ / CX und WRL werden weiterhin unterstützt. Für neue Projekte, empfehlen wir [ C++"/ WinRT"](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt), die basiert vollständig auf Standard C++ und bietet schnellere Leistung.

## <a name="desktop-bridge"></a>Desktop-Brücke

In Windows 10 können Sie Ihrer vorhandenen Desktopanwendung oder COM-Objekt als eine UWP-app-Paket und UWP-Features wie z. B. Touch hinzufügen oder APIs aus dem Satz der modernen Windows-API aufrufen. Sie können auch eine UWP-app hinzufügen, um eine desktop-Lösung in Visual Studio, und sie in einem einzelnen Paket und Windows-APIs verwenden, um die Kommunikation zwischen ihnen.

Visual Studio 2017 Version 15.4 und höher ermöglicht das Erstellen eines Windows-Anwendungsprojekts Paket zum Packen Ihrer vorhandenen Desktopanwendung Arbeit erheblich vereinfachen. Einige Einschränkungen gelten für die Registrierung aufrufen oder APIs, die desktop-Anwendung verwenden kann. In vielen Fällen können Sie jedoch den alternativen Codepfade, um ähnliche Funktionalität zu erzielen, während der Ausführung in einem app-Paket erstellen. Weitere Informationen finden Sie unter [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="games"></a>Spiele

DirectX-Spiele können auf dem PC oder der Xbox ausgeführt werden. Weitere Informationen finden Sie unter [DirectX-Grafiken und-Spiele](/windows/desktop/directx).

## <a name="sql-server-database-clients"></a>SQL Server-Datenbank-clients

Verwenden Sie den Zugriff auf SQL Server-Datenbanken von nativem Code ODBC- oder OLE DB. Weitere Informationen finden Sie unter [SQL Server Native Client](/sql/relational-databases/native-client/odbc/sql-server-native-client-odbc).

## <a name="windows-device-drivers"></a>Windows-Gerätetreiber

Treiber sind Low-Level-Komponenten, die Daten von Hardwaregeräten für Anwendungen zugänglich zu machen und andere Komponenten des Betriebssystems. Weitere Informationen finden Sie unter [Windows-Treiberkit (WDK)](/windows-hardware/drivers/index).

## <a name="windows-services"></a>Windows-Dienste

Eine Windows *Service* ist ein Programm, das im Hintergrund mit wenig oder ganz ohne Benutzereingriff ausgeführt werden kann. Diese Programme heißen *Daemons* auf UNIX-Systemen. Weitere Informationen finden Sie unter [Services](/windows/desktop/services/services).

## <a name="sdks-libraries-and-header-files"></a>SDKs, Bibliotheken und Headerdateien

Visual Studio enthält die C-Laufzeitbibliothek (CRT), die C++-Standardbibliothek und anderen Microsoft-spezifische Bibliotheken. Die Include-Ordner, die Headerdateien für diese Bibliotheken enthalten die meisten befinden sich in der Visual Studio-Installationsverzeichnis im Ordner \VC\. Die Windows- und CRT-Headerdateien befinden sich im Windows SDK-Installationsordner.

Die [Vcpkg-Paket-Manager](../build/vcpkg.md) können Sie bequem Hunderte von Drittanbieter-Open Source-Bibliotheken für Windows installieren.

Die Microsoft-Bibliotheken enthalten:

- Microsoft Foundation Classes (MFC): Ein objektorientiertes Framework zum Erstellen von herkömmlichen Windows-Programmen, besonders in Unternehmen eingesetzten Anwendungen, deren umfassender Benutzeroberflächen mit Schaltflächen, Listenfeldern, Strukturansichten und anderen Steuerelementen. Weitere Informationen finden Sie unter [MFC Desktop Applications](../mfc/mfc-desktop-applications.md).

- Active Template Library (ATL): Eine leistungsstarke Hilfebibliothek zum Erstellen von COM-Komponenten. Weitere Informationen finden Sie unter [ATL COM Desktop Components](../atl/atl-com-desktop-components.md).

- C++ AMP (C++ Accelerated Massive Parallelism): Eine Bibliothek, die leistungsstarke allgemeine Computerarbeit auf der GPU ermöglicht. Weitere Informationen finden Sie unter [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md).

- Concurrency Runtime: Eine Bibliothek, die die Arbeit der parallele und asynchrone Programmierung für Mehrkern- und mehr-Geräte vereinfacht. Weitere Informationen finden Sie unter [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

Viele Programmierszenarien bei Windows erfordern zudem das Windows SDK, in dem die Headerdateien enthalten sind, die den Zugriff auf Komponenten des Windows-Betriebssystems ermöglichen. Standardmäßig installiert Visual Studio das Windows SDK als Komponente von der C++-Desktop-Workload, die Entwicklung von universellen Windows-apps ermöglicht. Zum Entwickeln von UWP-apps benötigen Sie die Windows 10-Version des Windows SDK. Weitere Informationen finden Sie unter [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk). (Weitere Informationen zu Windows SDKs für frühere Versionen von Windows finden Sie unter den [Windows SDK-Archivs](https://developer.microsoft.com/windows/downloads/sdk-archive)).

**Programmieren von Dateien (x86) \Windows Kits** ist der Standardspeicherort für alle Versionen des Windows SDK, das Sie installiert haben.

Für andere Plattformen, wie Xbox und Azure, sind eigene SDKs verfügbar, die sie ggf. installieren müssen. Weitere Informationen finden Sie im DirectX-Developer Center sowie im Azure Developer Center.

## <a name="development-tools"></a>Entwicklungstools

Visual Studio bietet einen leistungsfähigen Debugger für nativen Code, Tools für statische Analyse, Grafikdebugtools, einen umfassenden Code-Editor, Unterstützung für Komponententests und viele weitere Tools und Hilfsprogramme. Weitere Informationen finden Sie unter [erste Schritte mit Visual Studio beim Entwickeln](/visualstudio/ide/get-started-developing-with-visual-studio), und [Übersicht von C++-Entwicklung in Visual Studio](../overview/overview-of-cpp-development.md).

## <a name="in-this-section"></a>In diesem Abschnitt
|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen eines Standard C++-Programms](walkthrough-creating-a-standard-cpp-program-cpp.md)| Erstellen Sie eine Windows-Konsolenanwendung.|
|[Exemplarische Vorgehensweise: Erstellen von Windows-Desktopanwendungen (C++)](walkthrough-creating-windows-desktop-applications-cpp.md)|Erstellen Sie eine systemeigene Windows-Desktopanwendung an.|
|[Windows-Desktopassistent](windows-desktop-wizard.md)|Mithilfe des Assistenten zum Erstellen von neuer Windows-Projekten.|
|[Active Template Library (ATL)](../atl/atl-com-desktop-components.md)|Verwenden Sie die ATL-Bibliothek, um COM-Komponenten in C++ zu erstellen.|
|[Microsoft Foundation Classes (MFC)](../mfc/mfc-desktop-applications.md)|Verwenden von MFC um zu große oder kleine ein Windows-Anwendungen mit Dialogfelder und Steuerelemente zu erstellen.|
|[Freigegebene ATL- und MFC-Klassen](../atl-mfc-shared/atl-mfc-shared-classes.md)|Verwenden Sie Klassen wie z. B. CString, die in ATL- und MFC-freigegeben werden.|
|[Datenzugriff](../data/data-access-in-cpp.md)| OLEDB- und ODBC|
|[Text und Zeichenfolgen](../text/text-and-strings-in-visual-cpp.md)|Verschiedene Zeichenfolgen-Datentypen für Windows.|
|[Ressourcen zum Erstellen eines Spiels mit DirectX](resources-for-creating-a-game-using-directx.md)
|[Vorgehensweise: Verwenden des Windows 10 SDK in einer Windows-Desktopanwendung](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows SDK|
|[Arbeiten mit Ressourcendateien](working-with-resource-files.md)|So fügen Sie Bilder, Symbole, Zeichenfolgentabellen und andere Ressourcen in eine Desktopanwendung.|
|[Ressourcen für das Erstellen eines Spiels mit DirectX (C++)](resources-for-creating-a-game-using-directx.md)|Enthält Links zu Inhalten für das Erstellen von Spielen in C++.|
|[Vorgehensweise: Verwenden des Windows 10 SDK in einer Windows-Desktopanwendung](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Enthält Schritte zum Einrichten Ihres Projekts für das Erstellen mit dem Windows 10-SDK.|
|[Bereitstellen nativer Desktopanwendungen](deploying-native-desktop-applications-visual-cpp.md)|Stellen Sie systemeigene Anwendungen für Windows bereit.|

## <a name="related-articles"></a>Verwandte Artikel

|Titel|Beschreibung|
|-----------|-----------------|
|[C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md)|Übergeordnetes Thema für Inhalte von Visual C++-Entwickler.|
[.NET-Entwicklung mit C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Erstellen von Wrappern für systemeigenen C++-Bibliotheken, die sie zur Kommunikation mit .NET-Anwendungen und-Komponenten zu aktivieren.|
|[Komponentenerweiterungen für .NET und UWP](../extensions/component-extensions-for-runtime-platforms.md)|Referenz für Syntaxelemente, die von C++ freigegebene c++ / CX und C++ / CLI.|
|[Universelle Windows-Apps (C++)](../cppcx/universal-windows-apps-cpp.md)|Schreiben von UWP-Anwendungen, die mithilfe C++ / CX oder Windows Runtime Template Library (WRL).|
|[C++-Attribute für COM und .NET](attributes/cpp-attributes-com-net.md)|Nicht standardmäßige Attribute für nur-Windows-Programmierung mit der .NET- oder COM.|
