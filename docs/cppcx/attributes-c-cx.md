---
title: Attribute (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 5f74914ab65fdf2c1803b47665e16378991efa3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209454"
---
# <a name="attributes-ccx"></a>Attribute (C++/CX)

Ein Attribut ist eine besondere Art von Ref-Klasse, die in eckigen Klammern auf Windows-Runtime-Typen und Methoden, um bestimmte Verhalten bei der Metadatenerstellung anzugeben vorangestellt werden kann. Mehrere vordefinierte Attribute, z. B. [Windows::Foundation::Metadata::WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)– werden häufig verwendet, in C++ / CX-Code. Dieses Beispiel zeigt, wie das Attribut auf eine Klasse angewendet wird:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Benutzerdefinierte Attribute

Sie können auch benutzerdefinierte Attribute definieren. Benutzerdefinierte Attribute müssen diese Windows-Runtime-Regeln entsprechen:

- Benutzerdefinierte Attribute können nur öffentliche Felder enthalten.

- Benutzerdefinierte Attributfelder können initialisiert werden, wenn das Attribut auf eine Klasse angewendet wird.

- Ein Feld kann einer dieser Typen sein:

   - int32 (int)

   - uint32 (int ohne Vorzeichen)

   - bool

   - Platform::String^

   - Windows::Foundation::HResult

   - Platform::Type^

   - öffentliche Enumerationsklasse (enthält benutzerdefinierte Enumerationen)

Das nächste Beispiel zeigt, wie ein benutzerdefiniertes Attribut definiert und anschließend zur Verwendung initialisiert wird.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Siehe auch

[Typsystem (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Sprachreferenz zu Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referenz zu Namespaces](../cppcx/namespaces-reference-c-cx.md)
