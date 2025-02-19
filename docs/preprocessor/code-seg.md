---
title: code_seg
ms.date: 11/04/2016
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: e566fb01bf70b343b75254a10466bdda2bc7ce1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403502"
---
# <a name="codeseg"></a>code_seg
Gibt das Textsegment an, in dem Funktionen in der OBJ-Datei gespeichert werden.

## <a name="syntax"></a>Syntax

```
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Parameter

**push**<br/>
(Optional) Legt einen Datensatz auf dem internen compilerstapel ab. Ein **Push** kann ein *Bezeichner* und *Segment-Name*.

**pop**<br/>
(Optional) Entfernt einen Datensatz von der obersten Position des internen Compilerstapels.

*identifier*<br/>
(Optional) Bei Verwendung mit **Push**, den Datensatz im internen compilerstapel ein Name zugewiesen. Bei Verwendung mit **pop**, Datensätze vom internen Stapel bis *Bezeichner* wird entfernt; Wenn *Bezeichner* wurde nicht gefunden im internen Stapel, nichts per pop ausgelesen wird.

*Bezeichner* ermöglicht, mehrere Datensätze mit nur einem entfernen **pop** Befehl.

"*Segment-Name*"<br/>
(Optional) Der Name eines Segments. Bei Verwendung mit **pop**, wird das Element im Stapel geholt und *Segment-Name* wird von der aktiven textsegmentnamen.

"*segment-class*"<br/>
(Optional) Ignoriert, aber aus Gründen der Kompatibilität mit früheren Versionen von C++ als Version 2.0.

## <a name="remarks"></a>Hinweise

Die **Code_seg** Pragmaanweisung steuert nicht die Platzierung von Objektcode, der für instanziierte Vorlagen generiert, oder von Code, die implizit vom Compiler generiert werden – beispielsweise spezielle Memberfunktionen. Wir empfehlen die Verwendung der [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) Attribut stattdessen, denn es Ihnen ermöglicht die Kontrolle über die Platzierung des gesamten Objektcodes. Dies umfasst vom Compiler generierten Code.

Ein *Segment* in einer OBJ-Datei ist einem benannten Block von Daten, die als eine Einheit in den Speicher geladen wird. Ein *Textsegment* ist ein Segment, das ausführbaren Code enthält. In diesem Artikel die Begriffe *Segment* und *Abschnitt* werden synonym verwendet.

Die **Code_seg** Pragmaanweisung teilt dem Compiler mit allen nachfolgenden Objektcode von der Übersetzungseinheit in ein Textsegment mit dem Namen einfügen *Segment-Name*. Standardmäßig wird das Textsegment, dass für Funktionen in einer OBJ-Datei verwendet wird, .text genannt.

Ein **Code_seg** Pragmaanweisung ohne Parameter setzt den textsegmentnamen für den nachfolgenden Objektcode auf .text zurück.

Sie können die [DUMPBIN. EXE-Datei](../build/reference/dumpbin-command-line.md) Anwendung zum Anzeigen der OBJ-Dateien. Versionen von DUMPBIN für jede unterstützte Zielarchitektur werden in Visual Studio enthalten.

## <a name="example"></a>Beispiel

Dieses Beispiel zeigt, wie Sie mit der **Code_seg** Pragma-Direktive, um zu steuern, wo der Objektcode platziert:

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

Eine Liste von Namen, die beim Erstellen eines Abschnitts nicht verwendet werden soll, finden Sie unter [/SECTION](../build/reference/section-specify-section-attributes.md).

Sie können auch Abschnitte für initialisierte Daten angeben ([Data_seg](../preprocessor/data-seg.md)), nicht initialisierte Daten ([Bss_seg](../preprocessor/bss-seg.md)), und const-Variablen ([Const_seg](../preprocessor/const-seg.md)).

## <a name="see-also"></a>Siehe auch

[code_seg (__declspec)](../cpp/code-seg-declspec.md)<br/>
[Pragma-Direktiven und das __Pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)