---
title: 'Multithreading: Gewusst wie: Verwenden Sie die MFC-Synchronisierungsklassen'
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
ms.openlocfilehash: 6115d942abc61fbfc9d60ca1ccf97d4b423ff7c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407691"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>Multithreading: Gewusst wie: Verwenden Sie die MFC-Synchronisierungsklassen

Die Synchronisierung des Zugriffs auf Ressourcen durch Threads ist ein häufiges Problem beim Schreiben von Multithreadanwendungen. Wenn zwei oder mehr Threads gleichzeitig auf dieselben Daten zugreifen, kann dies zu unerwünschten und unvorhersehbaren Ergebnissen führen. Es könnte z. B. vorkommen, dass der eine Thread den Inhalt einer Struktur aktualisiert, während der andere Thread gleichzeitig den Inhalt dieser Struktur liest. Es gibt keine Informationen darüber, welche Daten vom lesenden Thread in einem solchen Fall empfangen werden: die alten Daten, die neu geschriebenen Daten oder möglicherweise eine Kombination aus beidem. MFC enthält eine Reihe von Synchronisierungs- und Synchronisierungszugriffsklassen, die Sie bei der Lösung dieses Problems unterstützen. In diesem Thema werden die verfügbaren Klassen erläutert, und Sie erfahren, wie Sie diese in einer typischen Multithreadanwendung zum Erstellen von threadsicheren Klassen verwenden können.

Eine typische Multithreadanwendung enthält eine Klasse, die eine Ressource darstellt, die von Threads gemeinsam genutzt wird. Bei einer vorschriftsmäßig entwickelten, vollständig threadsicheren Klasse ist der Aufruf von Synchronisierungsfunktionen nicht erforderlich. Alles wird klassenintern geregelt, damit Sie sich auf die optimale Verwendung der Klasse konzentrieren können und nicht darauf, wie sie eventuell fehlerhaft werden könnte. Die beste Methode zum Erstellen einer vollständig threadsicheren Klasse ist die Einbindung der Synchronisierungsklasse in die Ressourcenklasse. Die Einbindung von Synchronisierungsklassen in eine gemeinsam genutzte Klasse ist ein einfacher Vorgang.

Als Beispiel wird eine Anwendung verwendet, in der eine verknüpfte Liste von Konten verwaltet wird. In dieser Anwendung können drei Konten in verschiedenen Fenstern untersucht werden, es kann jedoch nur jeweils ein Konto aktualisiert werden. Bei der Aktualisierung eines Kontos werden die aktualisierten Daten über das Netzwerk an ein Datenarchiv gesendet.

In dieser Beispielanwendung kommen alle drei Arten von Synchronisierungsklassen zum Einsatz. Da bis zu drei Konten gleichzeitig untersucht werden können, verwendet es [CSemaphore](../mfc/reference/csemaphore-class.md) Zugriff auf drei Ansichtsobjekte beschränkt. Beim Versuch, ein viertes Konto anzuzeigen, wartet die Anwendung entweder, bis eines der ersten drei Fenster geschlossen wird, oder der Versuch schlägt fehl. Wenn ein Konto aktualisiert wird, um die Anwendung verwendet [CCriticalSection](../mfc/reference/ccriticalsection-class.md) , stellen Sie sicher, dass nur ein Konto zu einem Zeitpunkt aktualisiert wird. Nach erfolgreicher Aktualisierung signalisiert sie [CEvent](../mfc/reference/cevent-class.md), die einen Thread für das Ereignis signalisiert wird, gibt. Dieser Thread sendet die neuen Daten an das Datenarchiv.

##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> Entwerfen einer threadsicheren Klasse

Um eine Klasse vollständig threadsicher zu gestalten, fügen Sie zunächst den gemeinsam genutzten Klassen die entsprechende Synchronisierungsklasse als Datenmember hinzu. Im vorherigen Beispiel kontoverwaltung eine `CSemaphore` Datenmember der Ansichtsklasse hinzugefügt werden würde eine `CCriticalSection` Datenmember der verknüpften Liste-Klasse hinzugefügt und eine `CEvent` Datenmember würde die Speicherklasse Daten hinzugefügt werden.

Fügen Sie anschließend allen Memberfunktionen, die die Daten in der Klasse ändern bzw. auf eine gesteuerte Ressource zugreifen, Synchronisierungsaufrufe hinzu. In jeder Funktion erstellen Sie entweder eine [CSingleLock](../mfc/reference/csinglelock-class.md) oder [CMultiLock](../mfc/reference/cmultilock-class.md) -Objekt und das Aufrufen dieses Objekts `Lock` Funktion. Wenn das `Unlock`-Objekt den Gültigkeitsbereich verlässt und zerstört wird, wird vom Destruktor des Objekts automatisch  aufgerufen und die Ressource freigegeben. Selbstverständlich können Sie `Unlock` auch direkt aufrufen.

Wenn Sie auf diese Art eine threadsichere Klasse entwerfen, kann sie in einer Multithreadanwendung ebenso problemlos wie eine nicht threadsichere Klasse verwendet werden, jedoch mit größerer Sicherheit. Wenn sowohl das Synchronisierungsobjekt als auch das Synchronisierungszugriffsobjekt in die Klasse der Ressource eingeschlossen werden, können Sie sämtliche Vorteile einer vollständig threadsicheren Programmierung nutzen, ohne Synchronisierungscode verwalten zu müssen.

Im folgenden Codebeispiel wird diese Methode anhand des `m_CritSection`-Datenmembers (vom Typ `CCriticalSection`) demonstriert, das in der gemeinsam genutzten Ressourcenklasse deklariert wurde; außerdem wird ein `CSingleLock`-Objekt verwendet. Der Versuch der Synchronisierung der gemeinsam genutzten Ressource (die von `CWinThread` abgeleitet wurde) wird durch Erstellung eines `CSingleLock`-Objekts unter Verwendung der Adresse des `m_CritSection`-Objekts unternommen. Nachdem die Ressource erfolgreich gesperrt wurde, wird das gemeinsam genutzte Objekt bearbeitet. Nachdem der Bearbeitungsvorgang abgeschlossen ist, wird die Ressource durch Aufruf von `Unlock` entsperrt.

```
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> Bei `CCriticalSection` steht im Gegensatz zu anderen MFC-Synchronisierungsklassen keine Option für eine zeitgesteuerte Sperranforderung zur Verfügung. Für die Zeit, die bis zur Freigabe eines Threads verstreichen kann, gibt es keinerlei Beschränkungen.

Der Nachteil dieses Ansatzes liegt darin, dass die Klasse etwas langsamer als die gleiche Klasse ohne hinzugefügte Synchronisierungsobjekte ist. Wenn das Objekt außerdem durch mehrere Threads gelöscht werden könnte, führt eine Einbindung nicht immer zum Erfolg. In dieser Situation ist es besser, separate Synchronisierungsobjekte zu verwalten.

Informationen zum bestimmen, welche Synchronisierungsklasse in verschiedenen Situationen verwendet, finden Sie unter [Multithreading: Wenn der Synchronisierungsklassen](multithreading-when-to-use-the-synchronization-classes.md). Weitere Informationen zur Synchronisierung finden Sie unter [Synchronisierung](/windows/desktop/Sync/synchronization) im Windows SDK. Weitere Informationen zur Multithreadunterstützung in MFC finden Sie unter [Multithreading mit C++ und MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Siehe auch

[Multithreading mit C++ und MFC](multithreading-with-cpp-and-mfc.md)
