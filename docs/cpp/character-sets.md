---
title: Zeichensätze
ms.date: 05/06/2019
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 92d60e3383abd7e3b3fa2d689958cf02a9b91e75
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222517"
---
# <a name="character-sets"></a>Zeichensätze

Der Text eines C++-Programms wird in Quelldateien gespeichert, die eine bestimmte Zeichencodierung verwenden. Der C++-Standard gibt einen einfachen Quellzeichensatz für Quelldateien und einen einfachen Ausführungszeichensatz für kompilierte Dateien an. Microsoft C++ Compiler (MSVC) können Sie einen zusätzlichen Satz von gebietsschemaspezifischen Zeichen in Quelldateien verwendet werden und kompilierten Dateien.

## <a name="character-sets"></a>Zeichensätze

Der C++-Standard gibt einen *einfachen Quellzeichensatz* an, der in Quelldateien verwendet werden kann. Es können zusätzliche Zeichen mithilfe eines *universellen Zeichennamens*angegeben werden, um Zeichen außerhalb dieses Satzes darzustellen. Beim Kompilieren stellen der *einfache Ausführungszeichensatz* und der *einfache Ausführungsbreitzeichensatz* die Zeichen und Zeichenfolgen dar, die in einem Programm angezeigt werden können. Die MSVC-Implementierung ermöglicht zusätzliche Zeichen im Quellcode und im kompilierten Code.

### <a name="basic-source-character-set"></a>Einfacher Quellzeichensatz

Der *einfache Quellzeichensatz* besteht aus 96 Zeichen, die in Quelldateien verwendet werden können. Dieser Satz umfasst das Leerzeichen, den horizontalen Tabstopp, den vertikalen Tabstopp, die Steuerzeichen für Seitenvorschub und Zeilenwechsel sowie diese Gruppe von Grafikzeichen:

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Microsoft-spezifisch**

MSVC enthält die `$` Zeichen als ein Mitglied des einfachen quellzeichensatzes. MSVC kann auch einen zusätzlichen Satz von Zeichen in Quelldateien verwendet werden, die auf Grundlage der dateicodierung. Standardmäßig speichert Visual Studio die Quelldateien mithilfe der Standardcodepage. Wenn Quelldateien mit einer Gebietsschema-Codepage oder eine Unicode-Codepage gespeichert werden, können Sie die Zeichen dieser Codepage in Ihrem Quellcode verwenden MSVC mit Ausnahme der Steuercodes, die im einfachen quellzeichensatz nicht explizit zugelassen festlegen. Beispielsweise können Sie japanische Zeichen in Kommentaren, Bezeichnern oder Zeichenfolgenliteralen einfügen, wenn Sie die Datei mit einer japanischen Codepage speichern. MSVC lässt keine Zeichenfolgen, die in gültige multibyte-Zeichen oder Unicode-Codepunkte übersetzt werden können. In Abhängigkeit von den Compileroptionen werden möglicherweise nicht alle zulässigen Zeichen in Bezeichnern angezeigt. Weitere Informationen finden Sie unter [Identifiers](../cpp/identifiers-cpp.md).

**Ende Microsoft-spezifisch**

### <a name="universal-character-names"></a>Universelle Zeichennamen

Da C++-Programme mehr Zeichen als die im einfachen Quellzeichensatz angegebenen Zeichen verwenden können, können Sie diese Zeichen mithilfe *universeller Zeichennamen*auf portierbare Weise angeben. Ein universeller Zeichennamen besteht aus einer Folge von Zeichen, die einen Unicode-Codepunkt darstellen.  Diese nehmen zwei Formen an. Verwenden Sie `\UNNNNNNNN` , um einen Unicode-Codepunkt der Form „U+NNNNNNNN“ darzustellen, wobei „NNNNNNNN“ die achtstellige hexadezimale Codepunktnummer angibt. Verwenden Sie das vierstellige `\uNNNN` , um einen Unicode-Codepunkt in der Form U+0000NNNN darzustellen.

Universelle Zeichennamen können in Bezeichnern und Zeichenfolgen sowie in Zeichenliteralen verwendet werden. Ein universeller Zeichennamen kann nicht dazu verwendet werden, um einen Ersatzcodepunkt im Bereich 0xD800-0xDFFF darzustellen. Verwenden Sie stattdessen den gewünschten Codepunkt. Der Compiler generiert automatisch alle erforderlichen Ersatzzeichen. Zusätzliche Einschränkungen gelten für die universellen Zeichennamen, die in Bezeichnern verwendet werden können. Weitere Informationen finden Sie unter [Identifiers](../cpp/identifiers-cpp.md) und [String and Character Literals](../cpp/string-and-character-literals-cpp.md).

**Microsoft-spezifisch**

Microsoft C++ -Compiler behandelt ein Zeichen in universellen Zeichennamens und in literalform Synonym verwenden lassen. Sie können z. B. einen Bezeichner in Form eines universellen Zeichennamens deklarieren und ihn dann in Literalform verwenden:

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Das Format von Sonderzeichen in der Windows-Zwischenablage ist von den Gebietsschemaeinstellungen der Anwendung abhängig. Das Ausschneiden und Einfügen dieser Zeichen in Ihren Code aus einer anderen Anwendung kann zu unerwarteten Zeichencodierungen führen. Dies kann in Ihrem Code ohne ersichtlichen Grund zu Analysefehlern führen. Es wird empfohlen, dass Sie für Ihre Quelldateicodierung eine Unicode-Codepage festlegen, bevor Sie Sonderzeichen einfügen. Außerdem wird empfohlen, dass Sie einen Eingabemethoden-Editor oder eine App zur Zeichenzuordnung verwenden, um Sonderzeichen zu generieren.

**Ende Microsoft-spezifisch**

### <a name="basic-execution-character-set"></a>einfache Ausführungszeichensatz

Der *einfache Ausführungszeichensatz* und der *einfache Ausführungsbreitzeichensatz* bestehen aus allen Zeichen des einfachen Quellzeichensatzes sowie aus den Steuerzeichen, die Warnung, Rücktaste, Wagenrücklauf und NULL darstellen. Der *Ausführungszeichensatz* und der *Ausführungsbreitzeichensatz* sind Obermengen der grundlegenden Sätze. Sie umfassen die durch die Implementierung definierten Quellzeichen außerhalb des einfachen Quellzeichensatzes. Der Ausführungszeichensatz weist eine gebietsschemaspezifische Darstellung auf.