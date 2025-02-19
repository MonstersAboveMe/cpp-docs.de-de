---
title: MFC-ActiveX-Steuerelemente
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
ms.openlocfilehash: d10aad92088a02a1cab0977ea174abdf919a05e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239696"
---
# <a name="mfc-activex-controls"></a>MFC-ActiveX-Steuerelemente

Ein ActiveX-Steuerelement ist eine wiederverwendbare Softwarekomponente, die auf dem Component Object Model (COM) basiert. Dieses Modell unterstützt zahlreiche OLE-Funktionen und kann an die unterschiedlichsten Softwareanforderungen angepasst werden.

>[!IMPORTANT]
> ActiveX ist eine veraltete Technologie, die nicht für Neuentwicklungen verwendet werden soll. Weitere Informationen finden Sie unter [ActiveX-Steuerelemente](activex-controls.md).

ActiveX-Steuerelemente sind sowohl für den herkömmlichen Einsatz in ActiveX-Steuerelementcontainern als auch für die Verwendung in World Wide Web-Seiten im Internet geeignet. Sie können ActiveX-Steuerelemente erstellen, entweder mit MFC, die hier beschrieben, sowie mit den [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md).

Ein ActiveX-Steuerelement kann sich in einem eigenen Fenster zeichnen, auf Ereignisse (wie Mausklicks) reagieren und über eine Schnittstelle verwaltet werden, die Eigenschaften und Methoden umfasst, die denen in den Automatisierungsobjekten ähneln.

Diese Steuerelemente können für viele Verwendungszwecke entwickelt werden, z. B. Datenbankzugriff, Datenüberwachung oder Diagrammerstellung. Neben ihrer Portabilität unterstützen ActiveX-Steuerelemente Funktionen, die zuvor nicht für ActiveX-Steuerelemente verfügbar waren, wie z. B. Kompatibilität mit vorhandenen OLE-Containern und die Möglichkeit, die Menüs in den OLE-Containermenüs zu integrieren. Außerdem unterstützt ein ActiveX-Steuerelement vollständig Automatisierung. Damit können für das Steuerelement Lese/Schreibeigenschaften und eine Reihe von Methoden sichtbar gemacht werden, die vom Benutzer des Steuerelements aufgerufen werden können.

Sie können fensterlose ActiveX-Steuerelemente und Steuerelemente erstellen, die nur dann ein Fenster erstellen, wenn sie aktiv sind. Fensterlose Steuerelemente beschleunigen die Anzeige der Anwendung. Außerdem können mit ihnen transparente und nicht rechteckige Steuerelemente erstellt werden. Sie können ActiveX-Steuerelement-Eigenschaften auch asynchron laden.

Ein ActiveX-Steuerelement wird als prozessinterner Server implementiert (in der Regel ein kleines Objekt), der in jedem OLE-Container verwendet werden kann. Beachten Sie, dass die volle Funktionalität eines ActiveX-Steuerelements nur verfügbar ist, wenn es innerhalb eines OLE-Containers verwendet wird, der in ActiveX-Steuerelementen berücksichtigt wird. Finden Sie unter [Port ActiveX-Steuerelementen in andere Anwendungen](../mfc/containers-for-activex-controls.md) eine Liste der Container, die ActiveX-Steuerelemente zu unterstützen. Dieser Containertyp (im Folgenden "Steuerelementcontainer" genannt) kann ein ActiveX-Steuerelement ausführen. Dazu werden die Eigenschaften und Methoden des Steuerelements verwendet und Benachrichtigungen aus dem ActiveX-Steuerelement in Form von Ereignissen empfangen. Dies wird in der folgenden Abbildung veranschaulicht.

![Zusammenspiel von ActiveX-Steuerelementcontainer und-Steuerelement](../mfc/media/vc37221.gif "Zusammenspiel von ActiveX-Steuerelementcontainer und-Steuerelement") <br/>
Interaktion zwischen einem ActiveX-Steuerelement-Container und einem ActiveX-Steuerelement mit Fenster

Einige neue Informationen zum Optimieren der ActiveX-Steuerelemente, finden Sie unter [MFC-ActiveX-Steuerelemente: Optimierung](../mfc/mfc-activex-controls-optimization.md).

Um ein MFC-ActiveX-Steuerelement erstellen zu können, finden Sie unter [erstellen ein ActiveX-Steuerelementprojekts](../mfc/reference/mfc-activex-control-wizard.md).

Weitere Informationen finden Sie unter:

- [ActiveX-Steuerelementcontainer](../mfc/activex-control-containers.md)

- [Aktive Dokumente](../mfc/active-documents.md)

- [Grundlegendes zu ActiveX-Steuerelementen](/windows/desktop/com/activex-controls)

- [Upgrading eines vorhandenen ActiveX-Steuerelements auf das Internet verwendet werden](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a> Grundlegende Komponenten eines ActiveX-Steuerelements

Ein ActiveX-Steuerelement verwendet mehrere Programmierelemente, um effizient mit einem Steuerelementcontainer und mit dem Benutzer interagieren zu können. Hierbei handelt es sich um Klasse [COleControl](../mfc/reference/colecontrol-class.md), ein Satz von Funktionen für Ereignisse auslösen und eine Dispatchzuordnung zuordnen.

Jedes ActiveX-Steuerelementobjekt, das Sie entwickeln, erbt einen leistungsfähigen Satz an Funktionen aus der zugehörigen MFC-Basisklasse, `COleControl`. Zu diesen Funktionen gehören die direkte Aktivierung und Automatisierungslogik. `COleControl` kann das Steuerelementobjekt mit derselben Funktionalität bereitstellen wie ein MFC-Fensterobjekt. Außerdem wird die Möglichkeit bereitgestellt, Ereignisse auszulösen. `COleControl` bieten auch [Fensterlose Steuerelemente](../mfc/providing-windowless-activation.md), bietet der ein Fenster der Container für die Unterstützung der Funktionalität abhängig (Mausauswahl, Tastaturfokus, Bildlauf), aber viel schnelleres anzeigen.

Da die Steuerelementklasse von `COleControl` abgeleitet wird, erbt sie die Fähigkeit, Nachrichten (sogenannte Ereignisse) zu senden oder auszulösen, wenn bestimmte Bedingungen erfüllt sind. Mithilfe dieser Ereignisse werden die Steuerelementcontainer benachrichtigt, wenn ein wichtiges Ereignis im Steuerelement auftritt. Sie können weitere Informationen zu einem Ereignis an den Steuerelementcontainer senden, indem Sie den Ereignissen Parameter anfügen. Weitere Informationen zu Ereignissen finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Ereignisse](../mfc/mfc-activex-controls-events.md).

Das letzte Element ist eine Dispatchzuordnung, mit der eine Reihe von Funktionen (sogenannte Methoden) und Attributen (sogenannte Eigenschaften) für den Benutzer des Steuerelements sichtbar gemacht werden. Anhand der Eigenschaften kann der Steuerelementcontainer oder der Benutzer des Steuerelements das Steuerelement auf vielfältige Weise manipulieren. Der Benutzer kann die Darstellung des Steuerelements und bestimmte Werte des Steuerelements ändern und Anforderungen an das Steuerelement senden, z. B. den Zugriff auf einen bestimmten Datenteil, der im Steuerelement gewartet wird. Diese Schnittstelle wird vom Steuerelemententwickler bestimmt und wird mit definiert **Klassenansicht**. Weitere Informationen über ActiveX-Steuerelement-Methoden und Eigenschaften finden Sie in den Artikeln [MFC-ActiveX-Steuerelemente: Methoden](../mfc/mfc-activex-controls-methods.md) und [Eigenschaften](../mfc/mfc-activex-controls-properties.md).

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> Interaktion zwischen Steuerelementen mit Windows und ActiveX-Steuerelementcontainer

Wenn ein Steuerelement in einem Steuerelementcontainers verwendet wird, werden zwei Kommunikationsmechanismen verwendet: Es macht Eigenschaften und Methoden verfügbar, und es löst Ereignisse aus. Die folgende Abbildung zeigt, wie diese beiden Mechanismen implementiert werden.

![ActiveX-Steuerelement kommuniziert mit seinem Container](../mfc/media/vc37222.gif "ActiveX-Steuerelement kommuniziert mit seinem Container") <br/>
Kommunikation zwischen einem ActiveX-Steuerelement-Container und einem ActiveX-Steuerelement

Die vorherige Abbildung zeigt auch, wie andere OLE-Schnittstellen (mit Ausnahme von Automatisierung und Ereignisse) von Steuerelementen behandelt werden.

Die gesamte Kommunikation eines Steuerelements mit dem Container wird durch `COleControl` ausgeführt. Behandelt einige der Anforderungen des Containers, `COleControl` wird Memberfunktionen aufrufen, die in der Steuerelementklasse implementiert werden. Alle Methoden und einige Eigenschaften werden auf diese Weise behandelt. Die Klasse des Steuerelements kann die Kommunikation mit dem Container durch Aufrufen von Memberfunktionen von `COleControl` auch initiieren. Ereignisse werden auf diese Weise ausgelöst.

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> Aktive und inaktive Zustände eines ActiveX-Steuerelements

Ein Steuerelement verfügt über zwei grundlegende Zustände: aktiv und inaktiv. In der Vergangenheit unterschieden sich diese Zustände dadurch, ob das Steuerelement ein Fenster hatte oder nicht. Ein aktives Steuerelement wies ein Fenster auf, ein inaktives Steuerelement wies kein Fenster auf. Mit der Einführung der fensterlose Aktivierung, ist diese Unterscheidung nicht mehr universell, gilt aber weiterhin für viele Steuerelemente.

Wenn eine [fensterloses Steuerelement](../mfc/providing-windowless-activation.md) aktiv wird, ruft er die Mausauswahl, Tastaturfokus, Bildlauf und andere Fensterdienste aus seinem Container. Sie können auch [Mausinteraktion für die inaktiven Steuerelemente bereitstellen](../mfc/providing-mouse-interaction-while-inactive.md)sowie Steuerelemente erstellen [warten, bis Sie zum Erstellen eines Fensters aktiviert](../mfc/turning-off-the-activate-when-visible-option.md).

Wenn ein Steuerelement mit einem Fenster aktiv wird, ist es möglich, vollständig mit dem Steuerelementcontainer, dem Benutzer und Windows zu interagieren. Die folgende Abbildung zeigt die Pfade der Kommunikation zwischen dem ActiveX-Steuerelement, dem Steuerelementcontainer und dem Betriebssystem.

![Meldungsverarbeitung in ActiveX-Steuerelement mit aktiven Fenster](../mfc/media/vc37223.gif "Meldungsverarbeitung in ActiveX-Steuerelement mit aktiven Fenster") <br/>
Windows-Nachrichtenverarbeitung in einem ActiveX-Steuerelement mit Fenster (sofern aktiv)

##  <a name="_core_serializing_activex_elements"></a> Serialisierung

Die Möglichkeit, die Daten zu serialisieren, was manchmal auch als Persistenz bezeichnet wird, ermöglicht es dem Steuerelement, den Wert der Eigenschaften in einen permanenten Speicher zu schreiben. Steuerelemente können neu erstellt werden, indem der Zustand des Objekts aus dem Speicher gelesen wird.

Beachten Sie, dass ein Steuerelement nicht den Zugriff auf das Speichermedium garantiert. Stattdessen ist der Container des Steuerelements für die Bereitstellung des Steuerelements mit einem Speichermedium zuständig, das zu den entsprechenden Zeitpunkten verwendet werden kann. Weitere Informationen zur Serialisierung finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Serialisieren von](../mfc/mfc-activex-controls-serializing.md). Informationen zum Optimieren der Serialisierung finden Sie unter [Optimieren von Persistenz und Initialisierung](../mfc/optimizing-persistence-and-initialization.md) in ActiveX-Steuerelementen: Die Optimierung.

##  <a name="_core_installing_activex_control_classes_and_tools"></a> Installieren von ActiveX-Steuerelementklassen und-Werkzeugen

Wenn Sie Visual C++ installieren, werden die MFC-ActiveX-Steuerelementklassen und Laufzeit-DLLs der Verkaufs- und Debugversionen von ActiveX-Steuerelementen automatisch installiert, wenn ActiveX-Steuerelemente bei der Installation ausgewählt werden (sie werden standardmäßig aktiviert).

Standardmäßig werden die ActiveX-Steuerelementklassen und-Werkzeuge in den folgenden Unterverzeichnissen unter \Programme\Microsoft Visual Studio .NET installiert:

- **\Common7\Tools**

   Enthält die Testcontainerdateien (TstCon32.exe und entsprechende Hilfedateien).

- **\Vc7\atlmfc\include**

   Enthält die Includedateien, die für die Entwicklung von ActiveX-Steuerelementen mit MFC erforderlich sind.

- **\Vc7\atlmfc\src\mfc**

   Enthält den Quellcode für bestimmte ActiveX-Steuerelementklassen in MFC.

- **\Vc7\atlmfc\lib**

   Enthält die Bibliotheken, die für die Entwicklung von ActiveX-Steuerelementen mit MFC erforderlich sind.

Dazu gehören auch Beispiele für MFC-ActiveX-Steuerelemente. Weitere Informationen zu diesen Beispielen, finden Sie unter [Beispiele für Steuerelemente: MFC-basierte ActiveX-Steuerelemente](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](../mfc/user-interface-elements-mfc.md)
