---
title: wbuffer_convert-Klasse
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: d19abf74bd9f794bc39ce04e5ed22e360cde75b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410888"
---
# <a name="wbufferconvert-class"></a>wbuffer_convert-Klasse

Beschreibt einen Streampuffer, der die Übertragung von Elementen in einen bzw. aus einem Streampuffer steuert.

## <a name="syntax"></a>Syntax

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*Codecvt*|Das Facet [locale](../standard-library/locale-class.md), das das Konvertierungsobjekt darstellt.|
|*Elem*|Der Breitzeichen-Elementtyp.|
|*Merkmale*|Die mit *Elem* verknüpften Merkmale.|

## <a name="remarks"></a>Hinweise

Die Vorlagenklasse beschreibt einen Streampuffer, der die Übertragung der Elemente des Typs `_Elem` beschreibt, dessen Zeichenmerkmale durch die Klasse `Traits` beschrieben werden, und zwar zu und von einem Bytestreampuffer des Typs `std::streambuf`.

Konvertierung zwischen einer Sequenz von `Elem`-Werten und Multibytesequenzen erfolgt durch ein Objekt der Klasse `Codecvt<Elem, char, std::mbstate_t>`, das die Anforderungen des Facets `std::codecvt<Elem, char, std::mbstate_t>` für die Standardcodekonvertierung erfüllt.

Ein Objekt dieser Vorlagenklasse speichert:

- Ein Zeiger auf den entsprechenden zugrunde liegenden Bytestreampuffer

- Ein Zeiger auf das zugeordnete Konvertierungsobjekt (das freigegeben wird, wenn das [wbuffer_convert](../standard-library/wbuffer-convert-class.md)-Objekt
