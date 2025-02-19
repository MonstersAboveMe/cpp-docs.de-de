---
title: Planerrichtlinien
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: e2acfc199e7ad9edf3965dc8ccb4103eb615a66b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408003"
---
# <a name="scheduler-policies"></a>Planerrichtlinien

Dieses Dokument beschreibt die Rolle von Planerrichtlinien können in der Concurrency Runtime. Ein *Planerrichtlinie* steuert die Strategie, die der Planer zum Verwalten von Aufgaben verwendet. Betrachten Sie beispielsweise eine Anwendung, müssen einige Aufgaben, führen Sie auf `THREAD_PRIORITY_NORMAL` und führen Sie auf andere Aufgaben `THREAD_PRIORITY_HIGHEST`.  Sie können zwei Scheduler-Instanzen erstellen: einen, der angibt, die `ContextPriority` -Richtlinie mit `THREAD_PRIORITY_NORMAL` und ein anderes, der angibt, die gleiche Richtlinie, um `THREAD_PRIORITY_HIGHEST`.

Mithilfe von Planerrichtlinien können Sie teilen Sie die verfügbaren Ressourcen und weisen einen festen Satz von Ressourcen für jedes Zeitplanungsmodul. Betrachten Sie beispielsweise einen parallelen Algorithmus, der nicht mehr als vier Prozessoren skaliert. Sie können eine Planerrichtlinie erstellen, die seine Aufgaben aus, wenn Sie nicht mehr als vier Prozessoren gleichzeitig verwenden beschränkt.

> [!TIP]
>  Die Concurrency Runtime stellt einen Standardplaner bereit. Aus diesem Grund müssen Sie nicht in Ihrer Anwendung zu erstellen. Da der Taskplaner die Leistung Ihrer Anwendungen optimieren können, es wird empfohlen, zunächst die [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) oder [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md) möchten noch nicht mit der Concurrency Runtime.

Bei Verwendung der [CurrentScheduler](reference/currentscheduler-class.md#create), [Scheduler](reference/scheduler-class.md#create), oder [:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) Methode, um eine Planerinstanz zu erstellen, geben Sie einen [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) Objekt, das eine Auflistung von Schlüssel-Wert-Paare enthält, die das Verhalten des Zeitplanungsmoduls angeben. Die `SchedulerPolicy` Konstruktor nimmt eine Variable Anzahl von Argumenten. Das erste Argument ist die Anzahl von Richtlinienelementen vor, die Sie angeben. Die übrigen Argumente sind Schlüssel-Wert-Paare für jedes Richtlinienelement. Das folgende Beispiel erstellt eine `SchedulerPolicy` Objekt, das drei Richtlinienelemente angibt. Die Runtime verwendet die Standardwerte für die Richtlinienschlüssel, die nicht angegeben werden.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

Die [Concurrency:: PolicyElementKey](reference/concurrency-namespace-enums.md#policyelementkey) -Enumeration definiert die Richtlinienschlüssel, die mit der Aufgabenplanung verbunden sind. Die folgende Tabelle beschreibt die Richtlinienschlüssel und der Standardwert, den die Common Language Runtime für jede von ihnen verwendet werden.

|Richtlinienschlüssel|Beschreibung|Standardwert|
|----------------|-----------------|-------------------|
|`SchedulerKind`|Ein [concurrency::SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) -Wert, der den Typ der zum Planen von Aufgaben zu verwendenden Threads angibt.|`ThreadScheduler` (verwenden Sie normale Threads). Dies ist der einzige gültige Wert für diesen Schlüssel.|
|`MaxConcurrency`|Ein `unsigned int` Wert, der die maximale Anzahl von Parallelitätsressourcen angibt, die der Planer verwendet.|[concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources)|
|`MinConcurrency`|Ein `unsigned int` Wert, der die minimale Anzahl von Parallelitätsressourcen angibt, die der Planer verwendet.|`1`|
|`TargetOversubscriptionFactor`|Ein `unsigned int` Wert, der angibt, wie viele threads jeder Verarbeitungsressource zuzuordnen.|`1`|
|`LocalContextCacheSize`|Ein `unsigned int` Wert, der die maximale Anzahl von Kontexten, die zwischengespeichert werden, können in der lokalen Warteschlange eines einzelnen virtuellen Prozessoren angibt.|`8`|
|`ContextStackSize`|Ein `unsigned int` Wert, der angibt, die Größe des Stapels in Kilobyte, um für jeden Kontext zu reservieren.|`0` (verwenden Sie die standardmäßige Stapelgröße)|
|`ContextPriority`|Ein `int` Wert, der die Threadpriorität jeder Kontext angibt. Dies sind alle Werte, die Sie an übergeben können [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) oder `INHERIT_THREAD_PRIORITY`.|`THREAD_PRIORITY_NORMAL`|

|`SchedulingProtocol`| Ein [Concurrency:: SchedulingProtocolType](reference/concurrency-namespace-enums.md#schedulingprotocoltype) Wert, der angibt, die zu verwendenden Planungsalgorithmus. | `EnhanceScheduleGroupLocality`| | `DynamicProgressFeedback`| Ein [DynamicProgressFeedbackType](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) Wert, der angibt, ob Ressourcen gemäß Statistiken Statusinformationen angibt.<br /><br /> **Beachten Sie** legen Sie diese Richtlinie nicht auf `ProgressFeedbackDisabled` da er für die Verwendung von der Laufzeit reserviert ist. |`ProgressFeedbackEnabled`|

Jedes Zeitplanungsmodul verwendet eine eigene Richtlinie, beim Planen von Aufgaben. Die Richtlinien, die einem Zeitplanungsmodul zugeordnet sind wirken sich nicht auf das Verhalten anderer Planer aus. Sie können nicht zusätzlich die Planerrichtlinie ändern, nachdem Sie erstellt die `Scheduler` Objekt.

> [!IMPORTANT]
>  Verwenden Sie nur Planerrichtlinien, um die Attribute für Threads zu steuern, die die Common Language Runtime erstellt. Ändern Sie die Threadaffinität oder die Priorität des Threads, die von der Runtime erstellt werden, da, die nicht definiertem Verhalten führen möglicherweise nicht.

Wenn Sie nicht explizit eine zu erstellen, erstellt die Runtime einen Standardplaner für Sie. Wenn den Standard-Scheduler in Ihrer Anwendung verwenden möchten, aber Sie möchten, geben Sie eine Richtlinie für den Scheduler verwenden, rufen Sie die [:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) -Methode auf, bevor Sie parallelen Arbeitsvorgänge planen. Wenn Sie nicht Aufrufen der `Scheduler::SetDefaultSchedulerPolicy` -Methode, die Common Language Runtime verwendet die Standardrichtlinie aus der Tabelle Werte.

Verwenden der [Concurrency::CurrentScheduler::GetPolicy](reference/currentscheduler-class.md#getpolicy) und [Concurrency::Scheduler::GetPolicy](reference/scheduler-class.md#getpolicy) Methoden, um eine Kopie der Planerrichtlinie abzurufen. Die Richtlinienwerte fest, die Sie von diesen Methoden erhalten können die Richtlinienwerte unterscheiden, die Sie angeben, wenn Sie den Scheduler erstellen.

## <a name="example"></a>Beispiel

Um Beispiele zu untersuchen, die bestimmte Planerrichtlinien, zum Steuern des Verhaltens des Zeitplanungsmoduls verwenden, finden Sie unter [Vorgehensweise: Angeben von bestimmten Planerrichtlinien](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) und [Vorgehensweise: Erstellen von Agents, die bestimmte Planerrichtlinien verwenden](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>Siehe auch

[Aufgabenplanung](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Vorgehensweise: Angeben von bestimmten Planerrichtlinien](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Vorgehensweise: Erstellen von Agents, die bestimmte Planerrichtlinien verwenden](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
