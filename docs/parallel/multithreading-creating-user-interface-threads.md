---
title: 'Multithreading: Erstellen von MFC-UI-Threads'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: b2fb23bd502de87aefe01d91e2b0640ee3137b00
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504584"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>Multithreading: Erstellen von MFC-UI-Threads

Ein Benutzeroberflächenthread wird normalerweise verwendet, um unabhängig von Threads, die derzeit andere Teile der Anwendung ausführen, Benutzereingaben zu behandeln und um auf vom Benutzer generierte Ereignisse zu reagieren. Der Thread der Hauptanwendung, der in der von `CWinApp` abgeleiteten Klasse enthalten ist, ist bereits erstellt und wird automatisch gestartet. In diesem Thema werden die notwendigen Schritte zur Erstellung zusätzlicher Benutzeroberflächenthreads beschrieben.

Im ersten Schritt müssen Sie beim Erstellen eines Benutzeroberflächen-Threads ist beim Ableiten einer Klasse von [CWinThread](../mfc/reference/cwinthread-class.md). Müssen Sie deklarieren und implementieren Sie diese Klasse, wobei die [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) und [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) Makros. Die Klasse muss bestimmte Funktionen überschreiben und kann wiederum andere Funktionen überschreiben. Diese Funktionen und ihre Aufgaben werden in der folgenden Tabelle erläutert.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Zu überschreibende Funktionen bei der Erstellung eines Benutzeroberflächenthreads

|Funktion|Zweck|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|Führt Aufräumarbeiten durch, wenn der Thread beendet wird. Wird normalerweise überschrieben.|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|Führt die Instanzeninitialisierung des Threads durch. Muss überschrieben werden.|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|Führt die threadspezifische Leerlaufzeitverarbeitung durch. Wird normalerweise nicht überschrieben.|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|Filtert Meldungen, bevor sie an weitergeleitet werden `TranslateMessage` und `DispatchMessage`. Wird normalerweise nicht überschrieben.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|Fängt unbehandelte Ausnahmen ab, die von den Meldungs- und Befehlshandlern des Threads ausgelöst werden. Wird normalerweise nicht überschrieben.|
|[Run](../mfc/reference/cwinthread-class.md#run)|Steuerungsfunktion für den Thread. Enthält die Meldungsverteilschleife. Wird selten überschrieben.|

in MFC werden durch Parameterüberladung zwei Versionen von `AfxBeginThread` zur Verfügung gestellt: eine, die nur Arbeitsthreads erstellen kann, und eine, die Benutzeroberflächenthreads oder Arbeitsthreads erstellen kann. Um Ihre Benutzeroberflächen-Thread zu starten, rufen Sie die zweite Überladung von [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), die folgenden Informationen angeben:

- Die [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) die Sie von abgeleiteten Klasse `CWinThread`.

- (Optional) Die gewünschte Prioritätsebene Standardmäßig ist normale Priorität eingestellt. Weitere Informationen zu den verfügbaren Prioritätsebenen finden Sie unter [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) im Windows SDK.

- (Optional) Die gewünschte Stapelgröße für den Thread. Standardmäßig wird die Größe des Erstellungsthreads verwendet.

- (Optional) CREATE_SUSPENDED, wenn der Thread in einem angehaltenen Zustand erstellt werden soll. Standardmäßig ist 0 eingestellt; Sie können den Thread auch normal starten.

- (Optional) Die gewünschten Sicherheitsattribute Standardmäßig werden dieselben Zugriffsrechte wie für den übergeordneten Thread verwendet. Weitere Informationen zum Format dieser Sicherheitsinformationen finden Sie unter [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) im Windows SDK.

Von `AfxBeginThread` wird der Großteil der Arbeit für Sie übernommen: Er erstellt ein neues Objekt der Klasse, initialisiert es mit den Informationen, die Sie angeben, und Aufrufe [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread) Starten der Ausführung des Threads. Während der gesamten Prozedur wird überprüft, ob alle Objekte ordnungsgemäß freigegeben werden, falls ein Teil des Erstellungsprozesses fehlschlagen sollte.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Multithreading: Terminieren von Threads](multithreading-terminating-threads.md)

- [Multithreading: Erstellen von Arbeitsthreads](multithreading-creating-worker-threads.md)

- [Prozesse und Threads](/windows/desktop/ProcThread/processes-and-threads)

## <a name="see-also"></a>Siehe auch

[Multithreading mit C++ und MFC](multithreading-with-cpp-and-mfc.md)
