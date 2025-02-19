---
title: Meldungshandler
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 0d3ed6239b638a0e161cd7e3580f4fe6e1b4a7e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383755"
---
# <a name="message-handlers"></a>Meldungshandler

In MFC, ein dediziertes *Handler* Funktion verarbeitet jede separate Nachricht. Meldungshandler-Funktionen werden die Memberfunktionen einer Klasse. In dieser Dokumentation werden die Begriffe verwendet *-Nachrichtenhandler-Memberfunktion*, *-Meldungshandler*, *Meldungshandler*, und *Handler*Synonym verwenden lassen. Einige Arten von Meldungshandler werden auch als "Befehlshandler." bezeichnet.

Das Message-Handler-Konten ein Großteil der Arbeit beim Schreiben einer Framework-Anwendung schreiben. In diesen Abschnitten wird beschrieben, wie der Mechanismus für die Verarbeitung von Nachrichten funktioniert.

Funktionsweise den Handler für eine Nachricht dafür ist, was als Reaktion auf diese Nachricht geschehen soll. Sie können die Handler erstellen, indem Sie das Fenster "Eigenschaften" der Klasse, und geben Sie dann in der Handler-Code, die mithilfe der Quellcode-Editor.

Sie können alle Funktionen von Microsoft Visual C++ und MFC verwenden, die Handler zu schreiben. Eine Liste aller Klassen, finden Sie unter [Übersicht über die Klassenbibliothek](../mfc/class-library-overview.md) in die *MFC-Referenz*.

## <a name="see-also"></a>Siehe auch

[Meldungen und Befehle im Framework](../mfc/messages-and-commands-in-the-framework.md)
