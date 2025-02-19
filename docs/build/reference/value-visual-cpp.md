---
title: '&lt;Wert > (C++-Dokumentationskommentare)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: c0863b41791254992d16d373328ff6c8a5d6f94f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317028"
---
# <a name="ltvaluegt"></a>&lt;value&gt;

Mit dem Tag \<value> können Sie Eigenschaften und Eigenschaftenaccessormethoden beschreiben. Beachten Sie, dass beim Hinzufügen einer Eigenschaft mithilfe eines Code-Assistenten in der Visual Studio-IDE der neuen Eigenschaft ein [\<summary>](summary-visual-cpp.md)-Tag hinzugefügt wird. Sie sollten dann manuell ein \<value>-Tag hinzufügen, um den Wert zu beschreiben, den die Eigenschaft darstellt.

## <a name="syntax"></a>Syntax

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parameter

*property-description*<br/>
Eine Beschreibung der Eigenschaft

## <a name="remarks"></a>Hinweise

Dokumentationskommentare werden zu einer Datei verarbeitet, indem sie mit [/doc](doc-process-documentation-comments-c-cpp.md) kompiliert werden.

## <a name="example"></a>Beispiel

```
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>Siehe auch

[XML-Dokumentation](xml-documentation-visual-cpp.md)
