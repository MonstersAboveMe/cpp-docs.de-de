---
title: ON_UPDATE_COMMAND_UI Macro
ms.date: 11/04/2016
f1_keywords:
- ON_UPDATE_COMMAND_UI
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- update handlers [MFC]
- command-handler macros
- updating user-interface objects [MFC]
ms.assetid: 3e72b50f-4119-4c82-81cf-6e09b132de05
ms.openlocfilehash: 986bc4f12223048a20f88da5d164b24dc1c08ace
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385351"
---
# <a name="onupdatecommandui-macro"></a>ON_UPDATE_COMMAND_UI Macro

Verwenden der **Eigenschaften** Fenster aus, um die Verbindung mit Befehlsaktualisierungs Handler in einer Befehlszielobjekt ein Benutzeroberflächen-Objekt. Es wird automatisch verbinden die Benutzeroberflächen-ID des Objekts mit der ON_UPDATE_COMMAND_UI-Makro und erstellen Sie einen Ereignishandler in das Objekt, das Update behandelt wird. Finden Sie unter [Zuordnen von Meldungen zu Funktionen](../mfc/reference/mapping-messages-to-functions.md) für Weitere Informationen.

Um einen Befehl alle Löschen Ihres Programms Menü "Bearbeiten" zu aktualisieren, verwenden Sie z. B. die **Eigenschaften** Fenster eine Meldungszuordnungseintrags in der ausgewählten Klasse eine Funktionsdeklaration für ein Befehlsaktualisierungshandler hinzufügen mit der Bezeichnung `OnUpdateEditClearAll` in der Klasse Deklaration und eine leere Funktion-Vorlage in der Implementierungsdatei der Klasse. Der Funktionsprototyp sieht folgendermaßen aus:

[!code-cpp[NVC_MFCDocView#2](../mfc/codesnippet/cpp/on-update-command-ui-macro_1.h)]

Wie alle Handler, die Funktion zeigt die **Afx_msg** Schlüsselwort. Wie alle Handler zu aktualisieren, nimmt er ein Argument, ein Zeiger auf eine `CCmdUI` Objekt.

## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Aktualisieren von Benutzeroberflächenobjekten](../mfc/how-to-update-user-interface-objects.md)
