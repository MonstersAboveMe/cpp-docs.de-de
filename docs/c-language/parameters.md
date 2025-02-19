---
title: Parameter
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function parameters
- parameters [C++]
- function arguments, vs. parameters
- parameters [C++], function
- functions [C], parameters
- function parameters, syntax
- ellipses (...), parameters
- '... ellipsis'
ms.assetid: 8f2b8026-78b5-4e21-86a3-bf0f91f05689
ms.openlocfilehash: 0652fe6076899020050d94378649018721b4b188
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147229"
---
# <a name="parameters"></a>Parameter

Argumente sind Namen von Werten, die einer Funktion durch einen Funktionsaufruf übergeben werden. Parameter sind die Werte, deren Empfang die Funktion erwartet. In einem Funktionsprototyp enthalten die Klammern nach dem Funktionsnamen eine vollständige Liste der Funktionsparameter und ihrer Typen. Parameterdeklarationen geben die Typen, Größen und Bezeichner der Werte an, die in den Parametern gespeichert sind.

## <a name="syntax"></a>Syntax

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* ist Microsoft-spezifisch \*/

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:/\* Ein Funktionsdeklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)** /\* Neuer Deklarator \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)** /\* Veralteter Deklarator \*/

*parameter-type-list*: /\* Die Parameterliste \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **, ...**

*parameter-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-list* **,**  *parameter-declaration*

*parameter-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *abstract-declarator*<sub>opt</sub>

Die *parameter-type-list* ist eine Folge von Parameterdeklarationen, die durch Trennzeichen getrennt sind. Die Form jedes Parameters in einer Parameterliste sieht wie folgt aus:

```C
[register]  type-specifier [declarator]
```

Funktionsparameter, die mit dem Attribut **auto** deklariert sind, generieren Fehler. Die Bezeichner der Parameter werden im Funktionstext verwendet und beziehen sich auf die Werte, die der Funktion übergeben werden. Sie können die Parameter in einem Prototyp benennen, aber die Namen verlassen den Gültigkeitsbereich am Ende der Deklaration. Daher können Parameternamen in der Funktionsdefinition auf die gleiche Weise oder anders zugewiesen werden. Diese Bezeichner können im äußersten Block des Funktionstexts nicht neu definiert werden, sie können jedoch in inneren, geschachtelten Blöcken neu definiert werden, als wäre die Parameterliste ein einschließender Block.

Jedem Bezeichner in *parameter-type-list* muss der entsprechende Typspezifizierer vorangestellt werden, wie in diesem Beispiel gezeigt:

```C
void new( double x, double y, double z )
{
    /* Function body here */
}
```

Wenn mindestens ein Parameter in der Parameterliste auftritt, kann die Liste mit einem Komma enden, gefolgt von drei Punkten (**, ...**). Diese Konstruktion, die so genannte „Ellipsenschreibweise“, gibt eine variable Anzahl von Argumenten für die Funktion an. (Weitere Informationen finden Sie unter [Aufrufe mit einer variablen Anzahl von Argumenten](../c-language/calls-with-a-variable-number-of-arguments.md).) Allerdings muss ein Aufruf der Funktion über mindestens so viele Argumente verfügen wie Parameter vor dem letzten Komma vorhanden sind.

Wenn keine Argumente an die Funktion übergeben werden sollen, wird die Liste der Parameter durch das Schlüsselwort `void` ersetzt. Diese Verwendung von `void` unterscheidet sich von der Verwendung als Typspezifizierer.

Reihenfolge und Typ der Parameter, einschließlich aller Auslassungsnotationen, müssen in allen Funktionsdeklarationen (falls vorhanden) und in der Funktionsdefinition gleich sein. Die Typen der Argumente nach üblichen arithmetische Konvertierungen müssen mit den Typen der entsprechenden Parameter zuweisungskompatibel sein. (Weitere Informationen zu arithmetischen Konvertierungen finden Sie unter [Übliche arithmetische Konvertierungen](../c-language/usual-arithmetic-conversions.md).) Die Argumente, die den Auslassungszeichen folgen, werden nicht überprüft. Basis, Struktur, Union, Zeiger oder Arraytyp eines Parameters können beliebig sein.

Der Compiler führt die üblichen arithmetischen Konvertierungen unabhängig für jeden Parameter und ggf. für jedes Argument aus. Nach der Konvertierung ist kein Parameter kürzer als `int`, und kein Parameter verfügt über einen **float**-Typ, es sei denn, der Parametertyp ist explizit als **float** im Prototyp angegeben. Dies bedeutet beispielsweise, dass die Deklaration eines Parameters als `char` denselben Effekt hat wie eine Deklaration als `int`.

## <a name="see-also"></a>Siehe auch

[C-Funktionsdefinitionen](../c-language/c-function-definitions.md)
