---
title: unorm_2-Klasse
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator+=
- amp_short_vectors/Concurrency::graphics::unnorm_2::y
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::x
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator--
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator*=
- amp_short_vectors/Concurrency::graphics::unnorm_2::xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator=
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::rg
- amp_short_vectors/Concurrency::graphics::unorm_2
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-=
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator/=
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::gr
- amp_short_vectors/Concurrency::graphics::unnorm_2::r
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::g
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator++
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
ms.openlocfilehash: 33411511809fc9798f6fdf65f5331e2e587990ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405494"
---
# <a name="unorm2-class"></a>unorm_2-Klasse

Stellt einen kurzen Vektor aus zwei normalen Zahlen ohne Vorzeichen dar.

## <a name="syntax"></a>Syntax

```
class unorm_2;
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[unorm_2-Konstruktor](#ctor)|Überladen. Standardkonstruktor, initialisiert alle Elemente mit 0.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|unorm_2::get_x||
|unorm_2::get_xy||
|unorm_2::get_y||
|unorm_2::get_yx||
|unorm_2::ref_g||
|unorm_2::ref_r||
|unorm_2::ref_x||
|unorm_2::ref_y||
|unorm_2::set_x||
|unorm_2::set_xy||
|unorm_2::set_y||
|unorm_2::set_yx||

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|unorm_2::operator--||
|unorm_2::operator*=||
|unorm_2::operator/=||
|unorm_2::operator++||
|unorm_2::operator+=||
|unorm_2::operator=||
|unorm_2::operator-=||

### <a name="public-constants"></a>Öffentliche Konstanten

|Name|Beschreibung|
|----------|-----------------|
|unorm_2::size-Konstante||

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|unorm_2::g||
|unorm_2::gr||
|unorm_2::r||
|unorm_2::rg||
|unorm_2:: x||
|unorm_2::xy||
|unorm_2::y||
|unorm_2::yx||

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`unorm_2`

## <a name="requirements"></a>Anforderungen

**Header:** amp_short_vectors.h

**Namespace:** Concurrency:: Graphics

##  <a name="ctor"></a> unorm_2

Standardkonstruktor, initialisiert alle Elemente mit 0.

```
unorm_2() restrict(amp,
    cpu);

unorm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

unorm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

unorm_2(
    unorm _V) restrict(amp,
    cpu);

explicit unorm_2(
    float _V) restrict(amp,
    cpu);

unorm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parameter

*_V0*<br/>
Der Wert, der 0-Element zu initialisieren.

*_V1*<br/>
Der Wert 1 Element initialisiert werden.

*_V*<br/>
Der Wert für die Initialisierung.

*_Other*<br/>
Das Objekt, das zum Initialisieren verwendet.

##  <a name="unorm_2__size"></a> Größe

```
static const int size = 2;
```

## <a name="see-also"></a>Siehe auch

[Concurrency::graphics Namespace](concurrency-graphics-namespace.md)
