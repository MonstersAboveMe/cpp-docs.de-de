---
title: Noexcept (C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noexcept_cpp
dev_langs: C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5068c7cf010c128fd7954ddfd356f49158bf6f17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/21/2017
---
# <a name="noexcept-c"></a>noexcept (C++)
**C ++ 11:** gibt an, ob eine Funktion Ausnahmen auslösen kann.  
  
## <a name="syntax"></a>Syntax  
  
> *Noexcept-Ausdruck*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**Noexcept (** *Konstantenausdruck* **)**  
  
### <a name="parameters"></a>Parameter  
 *konstanter Ausdruck*  
 Ein konstanter Ausdruck vom Typ `bool` , darstellt, ob der Satz von möglichen Ausnahmetypen leer ist. Die Version ist gleichbedeutend mit `noexcept(true)`.  
  
## <a name="remarks"></a>Hinweise  
 Ein *Noexcept Ausdruck* ist eine Art von *Ausnahmespezifikation*, ein Suffix, um die Deklaration einer Funktion, die einen Satz von Typen darstellt, die von einem Ausnahmehandler für jede Ausnahme abgeglichen werden kann, die beendet eine Funktion. Unäre Bedingungsoperator `noexcept(` *Constant_expression* `)` , in denen *Constant_expression* Yeilds `true`, und das Synonym bedingungslose `noexcept`, Geben Sie der Satz von möglichen Ausnahmetypen, die eine Funktion zu beenden, können leer ist. D. h. die Funktion löst nie eine Ausnahme aus und lässt nie eine Ausnahme von außerhalb ihres Bereichs weitergegeben werden. Der Operator `noexcept(` *Constant_expression* `)` , in denen *Constant_expression* Yeilds `false`, oder die Abwesenheit eine Ausnahmespezifikation (außer für eine Destruktor oder Aufheben der Funktion) gibt an, dass der Satz der möglichen Ausnahmen, die die Funktion verlassen, können die Menge aller Typen.  
 
 Markieren Sie eine Funktion als `noexcept` nur, wenn alle Funktionen, die es, entweder direkt oder indirekt aufgerufen, auch werden `noexcept` oder `const`. Der Compiler überprüft nicht unbedingt jeden Codepfad auf Ausnahmen, die bis zu auswirken können eine `noexcept` Funktion. Wenn eine Ausnahme, die außerhalb des Gültigkeitsbereichs einer Funktion markiert beendet wird `noexcept`, [Terminate](../standard-library/exception-functions.md#terminate) wird sofort aufgerufen, und es gibt keine Garantie, dass alle Objekte im Gültigkeitsbereich befindlichen Destruktoren aufgerufen werden. Verwendung `noexcept` anstelle des ausnahmespezifizierers dynamische `throw`, d. h. in C ++ 11 als veraltet markiert und höher und nicht vollständig in Visual Studio implementiert. Sollten Sie anwenden `noexcept` für alle Funktionen, die nie eine Ausnahme in der Aufrufliste weitergegeben ermöglicht. Wenn eine Funktion deklariert ist `noexcept`, dadurch, dass den Compiler effizienter Code in verschiedenen anderen Kontexten generieren.    
  
## <a name="example"></a>Beispiel  
Eine Vorlagenfunktion, die ihre Argumente kopiert deklariert werden möglicherweise `noexcept` unter der Voraussetzung, dass das kopierte Objekt eine einfache alte-Datentyp (POD) ist. Eine solche Funktion kann wie folgt deklariert werden:  
  
```cpp  
#include <type_traits>  
  
template <typename T>  
T copy_object(const T& obj) noexcept(std::is_pod<T>)  
{  
   // ...   
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Ausnahmebehandlung](../cpp/cpp-exception-handling.md) [Ausnahmespezifikationen (Throw, Noexcept)](../cpp/exception-specifications-throw-cpp.md)