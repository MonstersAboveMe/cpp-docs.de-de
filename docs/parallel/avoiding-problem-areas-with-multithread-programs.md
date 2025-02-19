---
title: Vermeiden von Problembereichen bei Multithreadprogrammen
ms.date: 11/04/2016
helpviewer_keywords:
- multithreading [C++], troubleshooting
- errors [C++], multithreaded programs
- threading [C++], troubleshooting
- troubleshooting [C++], multithreading
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
ms.openlocfilehash: 3ceae832599243ffa0aad2b6fa67148e7ea30510
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237063"
---
# <a name="avoiding-problem-areas-with-multithread-programs"></a>Vermeiden von Problembereichen bei Multithreadprogrammen

Es gibt mehrere Probleme, die auftreten können, erstellen, verknüpfen oder eine C-Multithreadprogramm ausführen. Einige der häufigsten Probleme werden in der folgenden Tabelle beschrieben. (Eine vergleichbare Erläuterung von MFC-Sicht, finden Sie unter [Multithreading: Tipps für die Programmierung](multithreading-programming-tips.md).)

|Problem|Mögliche Ursache|
|-------------|--------------------|
|Sie erhalten ein Meldungsfeld anzeigt, dass das Programm eine Schutz-Verletzung verursacht hat.|Verstöße gegen den Zugriffsschutz zu viele Win32-Programmierung-Fehlern führen. Eine häufige Ursache für den Schutz von Verletzungen ist die indirekte Zuweisung zu null-Zeiger. Da dies in Ihrem Programm auf Speicher zugreift, die nicht zu der er gehört führt, wird ein Schutz gegen ausgegeben.<br /><br /> Eine einfache Möglichkeit, um die Ursache eines Verstoßes Schutz zu erkennen ist, das Programm mit Debuginformationen kompiliert, und führen Sie es über den Debugger in Visual C++-Umgebung. Wenn der Schutzverletzungsfehler auftritt, Windows überträgt die Steuerung an den Debugger, und der Cursor befindet sich in der Zeile, die das Problem verursacht hat.|
|Das Programm generiert zahlreiche Fehler in der Kompilierung und Verknüpfung.|Sie können viele Probleme vermeiden, durch die Warnstufe des Compilers auf die höchsten Werte festlegen und die gewonnenen der Warnmeldungen an. Mit der Ebene 3 oder die Optionen für Warnung der Stufe 4, können Sie unbeabsichtigte datenkonvertierungen, fehlende Funktionsprototypen und Verwendung von nicht-ANSI-Funktionen erkennen.|

## <a name="see-also"></a>Siehe auch

[Multithreading bei C und Win32](multithreading-with-c-and-win32.md)
