---
title: 'Exemplarische Vorgehensweise: Hinzufügen eines CTaskDialog zu einer Anwendung'
ms.date: 04/25/2019
helpviewer_keywords:
- CTaskDialog, adding
- walkthroughs [MFC], dialogs
ms.assetid: 3a62abb8-2d86-4bec-bdb8-5784d5f9a9f8
ms.openlocfilehash: 8cf2223b2859a2dfa6ecc7582ec2f171a056152c
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558208"
---
# <a name="walkthrough-adding-a-ctaskdialog-to-an-application"></a>Exemplarische Vorgehensweise: Hinzufügen eines CTaskDialog zu einer Anwendung

In dieser exemplarische Vorgehensweise wird [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) vorgestellt, und Sie erfahren, wie Sie eine Ihrer Anwendung hinzufügen können.

Die `CTaskDialog` ist ein Aufgabendialogfeld angezeigt, die das Windows-Meldungsfeld in Windows Vista oder höher ersetzt. Der `CTaskDialog` verbessert das ursprüngliche Meldungsfeld und fügt Funktionen hinzu. Das Windows-Meldungsfeld wird weiterhin in Visual Studio unterstützt.

> [!NOTE]
> Windows-Versionen vor Windows Vista unterstützen nicht die `CTaskDialog`. Sie müssen eine alternative Dialogfeldoption programmieren, wenn Sie einem Benutzer eine Meldung anzeigen möchten, der Ihre Anwendung unter einer früheren Version von Windows ausführt. Sie können die statische Methode [CTaskDialog::IsSupported](../mfc/reference/ctaskdialog-class.md#issupported) verwenden, um zur Laufzeit zu bestimmen, ob der Computer eines Benutzers ein `CTaskDialog`ersetzt. Darüber hinaus ist der `CTaskDialog` nur verfügbar, wenn Ihre Anwendung mit der Unicode-Bibliothek erstellt wird.

Der `CTaskDialog` unterstützt mehrere optionale Elemente zum Sammeln und Anzeigen von Informationen. Ein `CTaskDialog` kann beispielsweise Befehlslinks, benutzerdefinierte Schaltflächen, benutzerdefinierte Symbole und eine Fußzeile anzeigen. Der `CTaskDialog` verfügt auch über mehrere Methoden, mit denen Sie den Status des Aufgabendialogfelds abfragen können, um festzustellen, welche optionalen Elemente der Benutzer ausgewählt hat.

## <a name="prerequisites"></a>Vorraussetzungen

Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:

- Visual Studio 2010 oder höher

- Windows Vista oder höher

## <a name="replacing-a-windows-message-box-with-a-ctaskdialog"></a>Ersetzen eines Windows-Meldungsfeld mit einem CTaskDialog

Das folgende Verfahren veranschaulicht die grundlegende Verwendung des `CTaskDialog`, sprich die Ersetzung des Windows-Meldungsfelds. In diesem Beispiel wird auch das Symbol geändert, das dem Aufgabendialogfeld zugeordnet ist. Ändern das Symbol wird die `CTaskDialog` gleichen auf das Windows-Meldungsfeld angezeigt.

### <a name="to-replace-a-windows-message-box-with-a-ctaskdialog"></a>So ersetzen Sie ein Windows-Meldungsfeld durch einen CTaskDialog

1. Verwenden der **MFS-Anwendungsassistenten** zum Erstellen einer MFC_Anwendung mit den Standardeinstellungen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Verwenden der neuen MFC-Shell-Steuerelemente](walkthrough-using-the-new-mfc-shell-controls.md) Anweisungen zum Öffnen des Assistenten für Ihre Version von Visual Studio.

1. Rufen sie *"meinProjekt"*. 

1. Verwenden Sie den **Projektmappen-Explorer** , die Datei „MyProject.cpp“ zu öffnen.

1. Fügen Sie nach der include-Liste `#include "afxtaskdialog.h"` ein.

1. Suchen Sie die Methode `CMyProjectApp::InitInstance`. Fügen Sie die folgenden Codezeilen vor der `return TRUE;` -Anweisung ein. Dieser Code erstellt die Zeichenfolgen, die wir im Windows-Meldungsfeld oder im `CTaskDialog`verwenden.

    ```cpp
    CString message("My message to the user");
    CString dialogTitle("My Task Dialog title");
    CString emptyString;
    ```

1. Fügen Sie den folgenden Code nach dem Code aus Schritt 4 ein. Dieser Code stellt sicher, dass der Computer des Benutzers den `CTaskDialog`unterstützt. Wenn das Dialogfeld nicht unterstützt wird, zeigt die Anwendung stattdessen ein Windows-Meldungsfeld an.

    ```cpp
    if (CTaskDialog::IsSupported())
    {

    }
    else
    {
        AfxMessageBox(message);
    }
    ```

1. Fügen Sie folgenden Code zwischen den Klammern hinter der `if` -Anweisung aus Schritt 5 ein. Dieser Code erstellt den `CTaskDialog`.

    ```cpp
    CTaskDialog taskDialog(message, emptyString, dialogTitle, TDCBF_OK_BUTTON);
    ```

1. Fügen Sie in der nächsten Zeile den folgenden Code ein. Dieser Code legt das Warnsymbol fest.

    ```cpp
    taskDialog.SetMainIcon(TD_WARNING_ICON);
    ```

1. Fügen Sie in der nächsten Zeile den folgenden Code ein. Dieser Code zeigt das Aufgabendialogfeld an.

    ```cpp
    taskDialog.DoModal();
    ```

Sie können Schritt 7 vermeiden, wenn Sie nicht möchten die `CTaskDialog` das gleiche Symbol wie das Windows-Meldungsfeld angezeigt. Wenn Sie diesen Schritt, das Vermeiden der `CTaskDialog` hat kein Symbol, wenn die Anwendung angezeigt wird.

Kompilieren Sie die Anwendung, und führen Sie sie aus. Die Anwendung zeigt das Aufgabendialogfeld nach dem Start an.

## <a name="adding-functionality-to-the-ctaskdialog"></a>Hinzufügen von Funktionen zum CTaskDialog

Das folgende Verfahren zeigt, wie Sie dem `CTaskDialog` Funktionen hinzufügen können, die Sie im vorherigen Verfahren erstellt haben. Der Beispielcode zeigt Ihnen, wie Sie bestimmte Anweisungen basierend auf der Auswahl des Benutzers ausführen.

### <a name="to-add-functionality-to-the-ctaskdialog"></a>So fügen Sie Funktionen zum CTaskDialog hinzu

1. Navigieren Sie zur **Ressourcenansicht**. Wenn Sie nicht angezeigt wird der **Ressourcenansicht**, können Sie es aus öffnen die **anzeigen** im Menü.

1. Erweitern Sie die **Ressourcenansicht** , bis Sie den Ordner **Zeichenfolgentabelle** auswählen können. Erweitern Sie ihn, und doppelklicken Sie auf den Eintrag **Zeichenfolgentabelle** .

1. Führen Sie einen Bildlauf zum unteren Rand der Tabelle durch, und fügen Sie einen neuen Eintrag hinzu. Ändern Sie die ID in `TEMP_LINE1`. Legen Sie **Befehlszeile 1**als Beschriftung fest.

1. Fügen Sie einen weiteren neuen Eintrag hinzu. Ändern Sie die ID in `TEMP_LINE2`. Legen Sie **Befehlszeile 2**als Beschriftung fest.

1. Navigieren Sie zurück zu „MyProject.cpp“.

1. Fügen Sie nach `CString emptyString;`den folgenden Code hinzu:

    ```cpp
    CString expandedLabel("Hide extra information");
    CString collapsedLabel("Show extra information");
    CString expansionInfo("This is the additional information to the user,\nextended over two lines.");
    ```

1. Suchen Sie die `taskDialog.DoModal()` -Anweisung, und ersetzen Sie sie durch den folgenden Code. Dieser Code aktualisiert das Aufgabendialogfeld und fügt neue Steuerelemente hinzu:

    ```cpp
    taskDialog.SetMainInstruction(L"Warning");
    taskDialog.SetCommonButtons(
        TDCBF_YES_BUTTON | TDCBF_NO_BUTTON | TDCBF_CANCEL_BUTTON);
    taskDialog.LoadCommandControls(TEMP_LINE1, TEMP_LINE2);
    taskDialog.SetExpansionArea(
        expansionInfo, collapsedLabel, expandedLabel);
    taskDialog.SetFooterText(L"This is the a small footnote to the user");
    taskDialog.SetVerificationCheckboxText(L"Remember your selection");
    ```

1. Fügen Sie die folgende Codezeile hinzu, die das Aufgabendialogfeld für den Benutzer anzeigt und die Auswahl des Benutzers abruft:

    ```cpp
    INT_PTR result = taskDialog.DoModal();
    ```

1. Fügen Sie nach dem Aufruf von `taskDialog.DoModal()`den folgenden Code ein. Mit diesem Codeabschnitt wird die Eingabe des Benutzers verarbeitet:

    ```cpp
    if (taskDialog.GetVerificationCheckboxState())
    {
        // PROCESS IF the user selects the verification checkbox
    }

    switch (result)
    {
    case TEMP_LINE1:
        // PROCESS IF the first command line
        break;
    case TEMP_LINE2:
        // PROCESS IF the second command line
        break;
    case IDYES:
        // PROCESS IF the user clicks yes
        break;
    case IDNO:
        // PROCESS IF the user clicks no
        break;
    case IDCANCEL:
        // PROCESS IF the user clicks cancel
        break;
    default:
        // This case should not be hit because closing
        // the dialog box results in IDCANCEL
        break;
    }
    ```

Ersetzen Sie im Code in Schritt 9 die Kommentare, die mit beginnen `PROCESS IF` durch den Code, der unter den angegebenen Bedingungen ausgeführt werden soll.

Kompilieren Sie die Anwendung, und führen Sie sie aus. Die Anwendung zeigt das Aufgabendialogfeld an, das die neuen Steuerelemente und zusätzliche Informationen verwendet.

## <a name="displaying-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>Anzeigen eines CTaskDialog, ohne ein CTaskDialog-Objekt zu erstellen

Das folgende Verfahren veranschaulicht, wie Sie ein `CTaskDialog` anzeigen, ohne zuvor ein `CTaskDialog` -Objekt erstellen zu müssen. Mit diesem Beispiel werden die vorherigen Prozeduren fortgesetzt.

### <a name="to-display-a-ctaskdialog-without-creating-a-ctaskdialog-object"></a>So zeigen Sie einen CTaskDialog an, ohne ein CTaskDialog-Objekt zu erstellen

1. Öffnen Sie die Datei "MyProject.cpp" aus, wenn es nicht bereits geöffnet ist.

1. Navigieren Sie zur schließenden Klammer für die `if (CTaskDialog::IsSupported())` -Anweisung.

1. Fügen Sie den folgenden Code direkt vor der schließenden Klammer der `if` -Anweisung (vor dem `else` -Block) ein:

    ```cpp
    HRESULT result2 = CTaskDialog::ShowDialog(L"My error message",
        L"Error",
        L"New Title",
        TEMP_LINE1,
        TEMP_LINE2);
    ```

Kompilieren Sie die Anwendung, und führen Sie sie aus. Die Anwendung zeigt zwei Aufgabendialogfelder an. Das erste Dialogfeld stammt aus dem **um hinzufügen-Funktionen zum CTaskDialog** Prozedur; das zweite Dialogfeld stammt aus der vorherigen Prozedur.

Diese Beispiele nicht alle verfügbaren Optionen für zeigen eine `CTaskDialog`, jedoch sollten Sie beim Einstieg zu helfen. Eine vollständige Beschreibung der Klasse finden Sie unter [CTaskDialog Class](../mfc/reference/ctaskdialog-class.md) .

## <a name="see-also"></a>Siehe auch

[Dialogfelder](../mfc/dialog-boxes.md)<br/>
[CTaskDialog-Klasse](../mfc/reference/ctaskdialog-class.md)<br/>
[CTaskDialog::CTaskDialog](../mfc/reference/ctaskdialog-class.md#ctaskdialog)
