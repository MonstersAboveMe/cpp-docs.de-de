---
title: Navigieren in C++-Code in Visual Studio
description: Verwenden Sie verschiedene Tools in Visual Studio, um in Ihrer C++-Codebasis zu navigieren.
ms.date: 05/28/2019
ms.openlocfilehash: 5f01307cc82fb1e61ba6fd0c922ea376279fba8b
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66742036"
---
# <a name="navigate-c-code-in-visual-studio"></a>Navigieren in C++-Code in Visual Studio

Visual Studio stellt mehrere Tools zur Verfügung, mit denen Sie schnell und effizient in Ihrer Codebasis navigieren können.

## <a name="open-an-included-file"></a>Öffnen einer enthaltenen Datei

Klicken Sie mit der rechten Maustaste auf eine `#include`-Anweisung, und wählen Sie **Zum Dokument wechseln** aus, oder drücken Sie **F12**, während der Cursor sich in der Zeile befindet, um die Datei zu öffnen.

![C&#43;&#43;-Menüoption „Zum Dokument wechseln“](../ide/media/go-to-document.png "Zum Dokument wechseln")

## <a name="toggle-headercode-file"></a>Umschalten zwischen Header- und Codedatei

Sie können zwischen einer Headerdatei und der entsprechenden Quelldatei wechseln, indem Sie mit der rechten Maustaste in die Datei klicken und **Header-/Codedatei umschalten** auswählen oder **STRG + K, STRG + O** drücken.

## <a name="go-to-definitiondeclaration"></a>Gehe zu Definition/Deklaration

Sie können zur Definition eines Codesymbols navigieren, indem Sie mit der rechten Maustaste in den Editor klicken und **Gehe zu Definition** auswählen oder indem Sie **F12** drücken. Sie können auf ähnliche Weise über das Kontextmenü zu einer Deklaration navigieren, oder indem Sie **STRG + F12** drücken.

![Gehe zu Definition in C&#43;&#43;](../ide/media/go-to-def.png "Gehe zu Definition")

## <a name="go-to"></a>Gehe zu

**Gehe zu** bezieht sich auf Navigationsfeatures, die basierend auf von Ihnen festgelegten Filtern jeweils eine spezifische Art Ergebnis erzielen. 

Sie können **Gehe zu** mit **STRG + ,** öffnen. Dies öffnet ein Suchfeld über dem Dokument, das Sie bearbeiten.

![Gehe zu in C&#43;&#43;](../ide/media/go-to-cpp.png "Gehe zu")

**Gehe zu** umfasst folgende Suchfilter:

- **Gehe zu Zeile (STRG + G):** Hiermit können Sie schnell zu einer anderen Zeile in Ihrem aktuellen Dokument springen
- **Gehe zu allen (STRG + ,)** oder **(STRG + T):** Suchergebnisse enthalten alles darunter befindliche
- **Gehe zu Datei (STRG + 1, F):** sucht in Ihrer Projektmappe nach Dateien
- **Gehe zu Typ (STRG + 1, T):** Suchergebnisse umfassen:
  - Klassen, Strukturen, Enumerationen
  - Schnittstellen & Delegate (nur verwalteter Code)
- **Gehe zu Member (STRG + 1, M):** Suchergebnisse umfassen:
  - Globale Variablen und globale Funktionen
  - Klassenmembervariablen und Memberfunktionen
  - Konstanten
  - Enumerationselemente
  - Eigenschaften und Ereignisse
- **Gehe zu Symbol (STRG + 1, S):** Suchergebnisse umfassen:
  - Ergebnisse von „Gehe zu Typ“ und „Gehe zu Member“
  - Alle verbleibenden C++-Sprachkonstrukte, einschließlich Makros

Beim ersten Aufruf von **Gehe zu** mit **STRG + ,** wird **Gehe zu allen** aktiviert (keine Filter für die Suchergebnisse). Anschließend können Sie gewünschte Filter mithilfe der Schaltflächen in der Nähe des Suchfelds auswählen. Sie können einen spezifischen Filter mithilfe der entsprechenden Tastenkombination aufrufen. Dadurch wird das Suchfeld **Gehe zu** mit dem jeweiligen Filter ausgewählt geöffnet. Alle Tastenkombinationen sind konfigurierbar.

Beginnen Sie Ihre Suchabfrage mit dem Zeichen des jeweiligen Filters gefolgt von einem Leerzeichen, um einen Textfilter anzuwenden. (Das Leerzeichen kann bei **Gehe zu Zeile** weggelassen werden.) Folgende Textfilter stehen zur Verfügung:

- Gehe zu allen: (kein Textfilter)
- Gehe zu Zeilennummer: :
- Gehe zu Datei: f
- Gehen zu Typ: t
- Gehe zu Member: m
- Gehe zu Symbol: #

Im folgenden Beispiel werden Suchergebnisse des Vorgangs *Gehe zu Datei* mit dem Filter „f“ veranschaulicht:

![Gehe zu Menü in C&#43;&#43;](../ide/media/vs2017-go-to-results.png "Gehe zu Menü")

Geben Sie ein „?“ gefolgt von einem Leerzeichen ein, um die Liste der Textfilter anzuzeigen. Sie können die **Gehe zu**-Befehle auch über das Menü **Bearbeiten** verwenden. Dort können Sie auch die jeweiligen Tastenkombinationen einsehen.

![Gehe zu Menü in C&#43;&#43;](../ide/media/go-to-menu-cpp.png "Gehe zu Menü")

## <a name="find--find-in-files"></a>Suchen/In Dateien suchen

Mit **Suchen (STRG + F)** oder **In Dateien suchen (STRG + UMSCHALT + F)** können Sie eine Textsuche in Ihrer Projektmappe durchführen.

Die Suche kann auf eine Auswahl, das aktuelle Dokument, alle offenen Dokumente, das aktuelle Projekt oder die gesamte Projektmappe begrenzt werden. Sie können reguläre Ausdrücke und Nur-Text verwenden. Alle Übereinstimmungen werden automatisch in der IDE hervorgehoben.

![Suchen in C&#43;&#43;](../ide/media/find-cpp.png "Suchen")

**In Dateien suchen** ist eine leistungsstärkere Version von **Suchen**, die Ergebnisse im Fenster **Suchergebnisse** anzeigt. Sie können externe Codeabhängigkeiten suchen, nach Dateitypen filtern usw. 

![In Dateien suchen in C&#43;&#43;](../ide/media/find-in-files-cpp.png "In Dateien suchen")

Sie können die Ergebnisse von **In Dateien suchen** in zwei Fenstern sortieren. Sie können Ergebnisse mehrerer Suchen aneinander anfügen. Klicken Sie auf ein Ergebnis, um zu dieser Position in der Datei zu springen.

![In Dateien suchen in C&#43;&#43;](../ide/media/vs2017-find-in-files-results.png "In Dateien suchen")

Weitere Informationen finden Sie in der Visual Studio-Dokumentation unter [Find in Files (In Dateien suchen)](/visualstudio/ide/find-in-files).

## <a name="find-all-references"></a>Alle Verweise suchen

Platzieren Sie das Caretzeichen in oder nach dem Symbol, klicken Sie dann mit der rechten Maustaste, und wählen Sie **Alle Verweise suchen** aus, um alle Vorkommnisse des Symbols in Ihrer Codebasis zu suchen. Sie können die Ergebnisse auf verschiedene Weisen filtern, sortieren oder gruppieren. Die Ergebnisse werden inkrementell aufgefüllt. Sie werden als Lese- oder Schreibvorgänge klassifiziert, damit Sie erkennen können, was sich in Ihrer Projektmappe befindet und was sich in Systemheadern oder anderen Bibliotheken befindet.

![Alle Verweise suchen in C&#43;&#43;](../ide/media/find-all-references-results-cpp.png "Alle Verweise suchen")

Sie können die Suchergebnisse anhand der folgenden Kategorien gruppieren:

- Projekt, dann Definition
- Nur Definition
- Definition, dann Projekt
- Definition, dann Pfad
- Definition, Projekt, dann Pfad

 #### <a name="filter-results"></a>Filtern der Ergebnisse

Zeigen Sie auf eine Spalte, und klicken Sie auf das angezeigte Filtersymbol, um die Ergebnisse zu filtern. Sie können die Ergebnisse der ersten Spalte Filtern, um beispielsweise Zeichenfolgen und Kommentarverweise zu filtern, die Sie möglicherweise nicht sehen möchten.

![Filter für Alle Verweise suchen in C&#43;&#43;](../ide/media/find-all-references-filters-cpp.png "Filter für Alle Verweise suchen")

- **Confirmed Results** (Bestätigte Ergebnisse): Tatsächliche Codeverweise auf das gesuchte Symbol. Beispielsweise gibt die Suche nach einer Memberfunktion namens `Size` alle Verweise auf `Size` zurück, die mit dem Bereich der Klasse übereinstimmt, die `Size` definiert.

- **Disconfirmed Results** (Nicht bestätigte Ergebnisse): Dieser Filter ist standardmäßig deaktiviert, da er Symbole mit übereinstimmenden Namen aufführt, die jedoch keine tatsächlichen Verweise auf das gesuchte Symbol sind. Wenn Sie zum Beispiel über zwei Klassen verfügen, die eine Memberfunktion namens `Size` definieren, und Sie eine Suche nach `Size` für einen Verweis eines Objekts von `Class1` durchführen, werden alle Verweise auf `Size` von `Class2` als nicht bestätigte Ergebnisse aufgeführt.

- **Unprocessed Results** (Nicht verarbeitete Ergebnisse): **Alle Verweise suchen** kann bei größeren Codebasen mehr Zeit beanspruchen, weshalb „nicht verarbeitete“ Ergebnisse hier aufgeführt werden. Nicht verarbeitete Ergebnisse weisen eine Übereinstimmung mit dem Namen des gesuchten Symbols auf, wurden jedoch noch nicht als tatsächliche Codeverweise bestätigt. Sie können diesen Filter aktivieren, um schneller Ergebnisse zu erhalten. Sie sollten sich jedoch bewusst sein, dass einige Ergebnisse möglicherweise keine tatsächlichen Verweise sind.

 #### <a name="sort-results"></a>Sortieren der Ergebnisse

Sie können die Ergebnisse nach einer beliebigen Spalte sortieren, indem Sie auf die jeweilige Spalte klicken. Sie können zwischen auf- und absteigender Reihenfolge wechseln, indem Sie ein weiteres Mal auf die Spalte klicken.

## <a name="navigation-bar"></a>Navigationsleiste

Sie können zur Definition eines Typs in einer Datei oder zu Typmembern navigieren, indem Sie die **Navigationsleiste** verwenden, die sich über dem Editorfenster befindet.

![C&#43;&#43;-Navigationsleiste](../ide/media/navbar-cpp.png "Navigationsleiste")

## <a name="see-also"></a>Siehe auch

[Read and understand C++ code (Lesen und Verstehen von C++-Code)](read-and-understand-code-cpp.md)</br>
[Schreiben und Umgestalten von Code (C++)](read-and-understand-code-cpp.md)</br>
[Collaborate with Live Share for C++ (Zusammenarbeit über Live Share für C++)](live-share-cpp.md)
