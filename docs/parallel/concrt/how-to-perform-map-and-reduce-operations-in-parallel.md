---
title: 'Vorgehensweise: Ausführen von Zuordnungs- und Reduzierungsoperationen Parallel'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: ba3ffb5cdae7dcc6f108f005fab33f9a1fee6a6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412708"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Vorgehensweise: Ausführen von Zuordnungs- und Reduzierungsoperationen Parallel

Dieses Beispiel zeigt, wie Sie mit der [Concurrency:: parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) und [Concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) Algorithmen und die [Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)Klasse, um die Vorkommen von Wörtern in Dateien gezählt.

Ein *Zuordnung* wendet eine Funktion auf jeden Wert in einer Sequenz. Ein *reduzieren* kombiniert die Elemente einer Sequenz in einen Wert. Sie können die C++-Standardbibliothek [Std](../../standard-library/algorithm-functions.md#transform) und [Std:: Accumulate](../../standard-library/numeric-functions.md#accumulate) Funktionen zum Ausführen von Zuordnungs- und reduzierungsvorgänge. Zur Verbesserung der Leistung bei vielen Problemen können Sie mit dem `parallel_transform`-Algorithmus parallel den Zuordnungsvorgang und mit dem `parallel_reduce`-Algorithmus parallel den Reduzierungsvorgang ausführen. In einigen Fällen können Sie mit `concurrent_unordered_map` die Zuordnung und Reduzierung in einem Vorgang durchführen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird das Vorkommen von Wörtern in Dateien gezählt. Er verwendet [Std:: vector](../../standard-library/vector-class.md) zur Darstellung des Inhalts von zwei Dateien. Der Zuordnungsvorgang berechnet das Vorkommen von jedem Wort in jedem Vektor. Der Reduzierungsvorang zählt die Wörter in den zwei Vektoren zusammen.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen `parallel-map-reduce.cpp` und führen Sie dann den folgenden Befehl in einem Fenster von Visual Studio-Eingabeaufforderung.

**/ EHsc CL.exe Parallel-Map-reduce.cpp**

## <a name="robust-programming"></a>Stabile Programmierung

In diesem Beispiel können Sie mit der in concurrent_unordered_map.h definierten `concurrent_unordered_map`-Klasse die Zuordnung und Reduzierung in einem Vorgang durchführen.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

In der Regel wird nur die äußere oder die innere Schleife parallel ausgeführt. Führen Sie die innere Schleife parallel aus, wenn Sie über relativ wenige Dateien mit vielen Wörtern verfügen. Führen Sie die äußere Schleife parallel aus, wenn Sie über relativ viele Dateien mit wenigen Wörtern verfügen.

## <a name="see-also"></a>Siehe auch

[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[Parallel_transform-Funktion](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[Parallel_reduce-Funktion](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map-Klasse](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
