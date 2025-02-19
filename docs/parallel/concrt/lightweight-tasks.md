---
title: Einfache Aufgaben
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 19918cf73c2b5b03db895c4751b22b1666ce01de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346356"
---
# <a name="lightweight-tasks"></a>Einfache Aufgaben

Dieses Dokument beschreibt die Rolle einfacher Aufgaben in der Concurrency Runtime. Ein *einfache Aufgabe* ist eine Aufgabe, die Sie direkt aus Planen einer `concurrency::Scheduler` oder `concurrency::ScheduleGroup` Objekt. Eine einfache Aufgabe ähnelt der Funktion, die für die Windows-API bereitgestellt [CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread) Funktion. Aus diesem Grund eignen sich einfache Aufgaben beim Anpassen von vorhandenen Codes, um die Planungsfunktionalität der Concurrency Runtime zu verwenden. Die Concurrency Runtime selbst verwendet einfache Aufgaben planen der asynchronen Agents und Senden von Nachrichten zwischen asynchronen Nachrichtenblöcken.

> [!TIP]
>  Die Concurrency Runtime stellt einen Standardplaner bereit. Sie müssen daher keinen in Ihrer Anwendung erstellen. Da der Taskplaner die Leistung Ihrer Anwendungen optimieren können, es wird empfohlen, zunächst die [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) oder [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md) möchten noch nicht mit der Concurrency Runtime.

Einfache Aufgaben erfordern einen geringeren Aufwand als asynchrone Agents und Aufgabengruppen. Z. B. informiert die Common Language Runtime Sie nicht, wenn eine einfache Aufgabe beendet ist. Darüber hinaus die Laufzeit abfangen oder nicht behandeln von Ausnahmen, die von einer einfachen Aufgabe ausgelöst werden. Weitere Informationen zur Behandlung von Ausnahmen und einfache Aufgaben finden Sie unter [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Für die meisten Aufgaben empfehlen wir, dass Sie stabiler Funktionen wie Aufgabengruppen und parallele Algorithmen, da sie Sie leichter können unterbrechen komplexe Aufgaben grundlegenderes zu. Weitere Informationen zu Aufgabengruppen finden Sie unter [Aufgabenparallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Weitere Informationen zu parallelen Algorithmen finden Sie unter [parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md).

Rufen Sie zum Erstellen einer einfachen Aufgabe der [Concurrency::ScheduleGroup::ScheduleTask](reference/schedulegroup-class.md#scheduletask), [Concurrency::CurrentScheduler::ScheduleTask](reference/currentscheduler-class.md#scheduletask), oder [Concurrency::Scheduler::ScheduleTask ](reference/scheduler-class.md#scheduletask) Methode. Warten, um auf den Abschluss einer einfachen Aufgabe warten, übergeordneten Zeitplanungsmoduls Herunterfahren, oder verwenden einen Synchronisierungsmechanismus, z. B. eine [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) Objekt.

## <a name="example"></a>Beispiel

Ein Beispiel, das veranschaulicht, wie vorhandener Code zur Verwendung einer einfachen Aufgabe angepasst wird, finden Sie unter [Exemplarische Vorgehensweise: Anpassen von vorhandenem Code Verwendung einfache Aufgaben](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>Siehe auch

[Aufgabenplanung](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Exemplarische Vorgehensweise: Anpassen von vorhandenem Code für die Verwendung einfacher Tasks](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
