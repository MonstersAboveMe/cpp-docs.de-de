---
title: Allgemeine Eigenschaften (Linux C++-Projekt) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: ce3683f11d80c253195b751b5eed364fbc04b68a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821280"
---
# <a name="general-properties-linux-c"></a>Allgemeine Eigenschaften (Linux C++)

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

Eigenschaft | Beschreibung | Auswahlmöglichkeiten
--- | ---| ---
Ausgabeverzeichnis | Gibt einen relativen Pfad zum Ausgabedateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Zwischenverzeichnis | Gibt einen relativen Pfad zum Zwischendateiverzeichnis an. Kann Umgebungsvariablen enthalten.
Target Name | Gibt einen Dateinamen an, den dieses Projekt generiert.
Zielerweiterung | Gibt eine Dateierweiterung an, die dieses Projekt generiert. (Beispiel: .a)
Bei der Bereinigung zu löschende Erweiterungen | Durch Semikolons getrennte Platzhalterspezifikation, die angibt, welche Dateien im Zwischenverzeichnis beim Bereinigen oder erneuten Erstellen gelöscht werden sollen.
Buildprotokolldatei | Gibt die zu schreibende Buildprotokolldatei an, wenn die Buildprotokollierung aktiviert ist.
Plattformtoolset | Gibt das Toolset zum Erstellen der aktuellen Konfiguration an. Wenn keine Angabe erfolgt, wird das Standardtoolset verwendet.
Remotebuildcomputer | Der Zielcomputer oder das Gerät, der bzw. das für den Remotebuild, die Bereitstellung und das Debuggen verwendet werden soll. **Visual Studio 2019 Version 16.1**: Auf der Seite zum [Debuggen](debugging-linux.md) kann ein anderer Debugcomputer angegeben werden.
Remotebuild-Stammverzeichnis | Gibt einen Pfad zu einem Verzeichnis auf dem Remotecomputer oder -Gerät an.
Remotebuild-Projektverzeichnis | Gibt einen Pfad zu einem Verzeichnis auf dem Remotecomputer oder -Gerät für das Projekt an.
Konfigurationstyp | Gibt den Typ der Ausgabe an, die diese Konfiguration generiert. | **Dynamische Bibliothek (.so)**: Dynamische Bibliothek (.so)<br>**Statische Bibliothek (.a)**: Statische Bibliothek (.a)<br>**Anwendung (.out)**: Anwendung (.out)<br>**Makefile**: Makefile<br>
Verwendung von STL | Gibt an, welche C++-Standardbibliothek für diese Konfiguration verwendet werden soll. | **Freigegebene GNU C++-Standardbibliothek**<br>**Statische GNU C++-Standardbibliothek (-static)**<br>

::: moniker-end

