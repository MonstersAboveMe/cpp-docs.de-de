---
title: Platzhaltererweiterung
ms.date: 11/04/2016
f1_keywords:
- _setargv
helpviewer_keywords:
- asterisk wildcard
- _setargv function
- command line [C++], processing arguments
- command line [C++], wildcards
- command-line wildcards
- question mark, wildcard
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
ms.openlocfilehash: 2d495f94f2e3fb7b88d235edc7b98f8e90775393
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209514"
---
# <a name="wildcard-expansion"></a>Platzhaltererweiterung

## <a name="microsoft-specific"></a>Microsoft-spezifisch

Sie können Platzhalter – das Fragezeichen (?) und das Sternchen (*) – verwenden, um Dateinamen- und Pfadargumente in der Befehlszeile anzugeben.

Befehlszeilenargumente werden durch eine Routine, die mit dem Namen behandelt `_setargv` (oder `_wsetargv` in der Breitzeichen-Umgebung), die standardmäßig Platzhalter in separate Zeichenfolgen im nicht erweitert die `argv` Zeichenfolgenarray. Weitere Informationen zum Aktivieren von platzhaltererweiterung finden Sie unter [Erweitern von Platzhalterargumenten](../c-language/expanding-wildcard-arguments.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[main: Programmstart](../cpp/main-program-startup.md)