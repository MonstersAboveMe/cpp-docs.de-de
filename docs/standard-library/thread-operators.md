---
title: '&lt;thread&gt;-Operatoren'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 5a2fd845598ac9f9c983bf53cbd7665ef66ffb70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412045"
---
# <a name="ltthreadgt-operators"></a>&lt;thread&gt;-Operatoren

||||
|-|-|-|
|[Operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a> operator&gt;=

Bestimmt, ob ein `thread::id`-Objekt größer als oder gleich einem anderen Objekt ist.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*<br/>
Das linke `thread::id`-Objekt.

*Rechts*<br/>
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left < Right)`

### <a name="remarks"></a>Hinweise

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_gt"></a> operator&gt;

Bestimmt, ob ein `thread::id`-Objekt größer als ein anderes Objekt ist.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*<br/>
Das linke `thread::id`-Objekt.

*Rechts*<br/>
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`Right < Left`

### <a name="remarks"></a>Hinweise

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_lt_eq"></a> operator&lt;=

Bestimmt, ob ein `thread::id`-Objekt kleiner als oder gleich einem anderen Objekt ist.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*<br/>
Das linke `thread::id`-Objekt.

*Rechts*<br/>
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Right < Left)`

### <a name="remarks"></a>Hinweise

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_lt"></a> operator&lt;

Bestimmt, ob ein `thread::id`-Objekt kleiner als ein anderes Objekt ist.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*<br/>
Das linke `thread::id`-Objekt.

*Rechts*<br/>
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**"true"** Wenn *Links* vorausgeht *rechts* in der gesamten Sortierung hingegen **"false"**.

### <a name="remarks"></a>Hinweise

Der Operator definiert eine gesamte Sortierung für alle `thread::id`-Objekte. Diese Objekte können als Schlüssel in assoziativen Containern verwendet werden.

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_neq"></a> operator!=

Überprüft zwei `thread::id`-Objekte auf Ungleichheit.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*<br/>
Das linke `thread::id`-Objekt.

*Rechts*<br/>
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

`!(Left == Right)`

### <a name="remarks"></a>Hinweise

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_eq_eq"></a> operator==

Überprüft zwei `thread::id`-Objekte auf Gleichheit.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parameter

*Links*<br/>
Das linke `thread::id`-Objekt.

*Rechts*<br/>
Das rechte `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

**"true"** aus, wenn die beiden Objekte den gleichen Ausführungsthread darstellen oder wenn kein Objekt einen Ausführungsthread darstellt, andernfalls **"false"**.

### <a name="remarks"></a>Hinweise

Diese Funktion löst keine Ausnahmen aus.

## <a name="op_lt_lt"></a> operator&lt;&lt;

Fügt eine Textdarstellung eines `thread::id`-Objekts in einen Stream ein.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parameter

*Ostr*<br/>
Ein [basic_ostream](../standard-library/basic-ostream-class.md)-Objekt.

*Id*<br/>
Ein `thread::id`-Objekt.

### <a name="return-value"></a>Rückgabewert

*Ostr*.

### <a name="remarks"></a>Hinweise

Diese Funktion fügt *Id* in *Ostr*.

Wenn zwei `thread::id`-Objekte gleich sind, sind die eingefügten Text-Darstellungen dieser Objekte gleich.

## <a name="see-also"></a>Siehe auch

[\<thread>](../standard-library/thread.md)<br/>
