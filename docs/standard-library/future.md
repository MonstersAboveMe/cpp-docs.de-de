---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: 189a9f16b65ae74fc2a86bee62bf8bd548c486aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159859"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

Schließen Sie den Standardheader \<future> ein, um Vorlagenklassen und unterstützende Vorlagen zu definieren, die das Ausführen einer Funktion – möglicherweise in einem separaten Thread – und das Abrufen des Ergebnisses vereinfachen. Das Ergebnis zeigt entweder den Wert, der von der Funktion zurückgegeben wird oder eine Ausnahme, die von der Funktion ausgegeben, aber nicht in der Funktion abgefangen wird.

Für diesen Header wird "Concurrency Runtime (ConcRT)" verwendet, sodass er zusammen mit anderen ConcRT-Mechanismen verwendet werden kann. Weitere Informationen finden Sie unter [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntax

```cpp
#include <future>
```

## <a name="remarks"></a>Hinweise

> [!NOTE]
> Im Code, der kompiliert wird **"/ CLR"**, dieser Header blockiert.

In einem *asynchronen Anbieter* wird das Ergebnis eines Funktionsaufrufs gespeichert. Ein a*synchrones Rückgabeobjekt* wird zum Abrufen des Ergebnisses eines Funktionsaufrufs verwendet. Ein *asynchroner zugeordneter Zustand* ermöglicht die Kommunikation zwischen einem asynchronen Anbieter und mindestens einem asynchronen Rückgabeobjekt.

Mit einem Programm werden nicht direkt zugeordnete asynchrone Zustandsobjekte erstellt. Mit dem Programm wird ein asynchroner Anbieter erstellt, wenn einer benötigt wird. Davon wird ein asynchrones Rückgabeobjekt erstellt, das dem Anbieter den asynchronen zugeordneten Zustand freigibt. Von asynchronen Anbietern und asynchronen Rückgabeobjekten werden Objekte zurückgegeben, die den freigegebenen zugeordneten asynchronen Zustand enthalten. Wenn das letzte Objekt, das den asynchronen zugeordneten Zustand verweist, diesen freigibt, wird das Objekt, das den asynchronen zugeordneten Zustand enthält, zerstört.

Ein asynchroner Anbieter oder ein asynchrones Rückgabeobjekt, das keinen verknüpften asynchronen Zustand aufweist, ist *leer*.

Ein zugeordneter asynchroner Zustand ist nur dann *bereit*, wenn sein asynchroner Anbieter einen Rückgabewert oder eine Ausnahme gespeichert hat.

Die Vorlagenfunktion `async` und die Vorlagenklassen `promise` sowie `packaged_task` sind asynchrone Anbieter. Mit den Vorlagenklassen `future` und `shared_future` werden asynchrone Rückgabeobjekte beschrieben.

Jede der Vorlagenklassen `promise`, `future`, und `shared_future` verfügt über eine Spezialisierung für den Typ **"void"** und eine teilweise Spezialisierung für das Speichern und Abrufen eines Werts durch einen Verweis. Diese Spezialisierungen unterscheiden sich von der primären Vorlage nur durch die Signaturen und die Semantik der Funktionen, die den zurückgegebenen Wert speichern und abrufen.

Die Vorlagenklassen `future` und `shared_future` nie-block, in deren Destruktoren, außer in einem Fall, das für die Abwärtskompatibilität beibehalten wird: Im Gegensatz zu anderen Futures für eine `future`– oder das letzte `shared_future`–, die Schritte mit der Aufgabe angefügt wird `std::async`, der Destruktor blockiert, wenn die Aufgabe nicht abgeschlossen wurde; das heißt, er blockiert, wenn dieser Thread nicht aufgerufen wurde `.get()` oder `.wait()`und die Aufgabe noch ausgeführt wird. Benutzerfreundlichkeit wird im folgenden Hinweis wurde in der Beschreibung der `std::async` im Draft Standard: "[Hinweis: Wenn eine Zukunft std::async abgerufenes außerhalb des lokalen Bereichs verschoben wird, muss anderer Code, die die Zukunft verwendet Beachten Sie, dass damit der Freigabezustand bereit. wird die Zukunft der Destruktor blockiert sein – Ende des Hinweises] "In allen anderen Fällen `future` und `shared_future` Destruktoren sind erforderlich und werden garantiert nie blockiert.

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|Name|Beschreibung|
|----------|-----------------|
|[future-Klasse](../standard-library/future-class.md)|Beschreibt ein asynchrones Rückgabeobjekt.|
|[future_error-Klasse](../standard-library/future-error-class.md)|Beschreibt ein Ausnahmeobjekt, das von Methoden des `future`-Objekte verwaltenden Typs ausgelöst werden.|
|[packaged_task-Klasse](../standard-library/packaged-task-class.md)|Beschreibt einen asynchronen Anbieter, der ein Aufrufwrapper ist und dessen Aufrufsignatur `Ty(ArgTypes...)` ist. Der zugehörige asynchrone Zustand enthält zusätzlich zum potentiellen Ergebnisses eine Kopie des aufrufbaren Objekts .|
|[promise-Klasse](../standard-library/promise-class.md)|Beschreibt einen asynchronen Anbieter.|
|[shared_future-Klasse](../standard-library/shared-future-class.md)|Beschreibt ein asynchrones Rückgabeobjekt. Im Gegensatz zu einem `future`-Objekt, kann ein asynchroner Anbieter beliebig vielen `shared_future`-Objekten zugeordnet werden.|

### <a name="structures"></a>Strukturen

|Name|Beschreibung|
|----------|-----------------|
|[is_error_code_enum-Struktur](../standard-library/is-error-code-enum-structure.md)|Spezialisierungen, die angeben, dass `future_errc` für das Speichern von `error_code` geeignet ist.|
|[uses_allocator-Struktur](../standard-library/uses-allocator-structure.md)|Spezialisierung, die immer "True" ist.|

### <a name="functions"></a>Funktionen

|Name|Beschreibung|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Stellt einen asynchronen Anbieter dar.|
|[future_category](../standard-library/future-functions.md#future_category)|Gibt einen Verweis auf das `error_category`-Objekt zurück, das Fehler bestimmt, die `future`-Objekten zugeordnet werden.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Erstellt ein `error_code`-Element, das das `error_category`-Objekt aufweist, das `future` Fehler bestimmt.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Erstellt ein `error_condition`-Element, das das `error_category`-Objekt aufweist, das `future` Fehler bestimmt.|
|[swap](../standard-library/future-functions.md#swap)|Tauscht den zugeordneten Zustand eines asynchronen `promise`-Objekts mit dem des anderen aus.|

### <a name="enumerations"></a>Enumerationen

|Name|Beschreibung|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Liefert symbolische Namen für die von der `future_error`-Klasse ausgegeben Fehler.|
|[future_status](../standard-library/future-enums.md#future_status)|Liefert symbolische Namen für die Gründe, aus denen eine zeitgesteuerte Wartefunktion eine Rückgabe ausführen kann.|
|[launch](../standard-library/future-enums.md#launch)|Stellt einen Bitmaskentyp dar, mit dem die möglichen Modi für die Vorlagenfunktion `async` beschrieben werden.|

## <a name="see-also"></a>Siehe auch

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)<br/>
