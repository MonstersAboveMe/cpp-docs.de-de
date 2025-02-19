---
title: '&lt;thread&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: c0a8e42cb7ee78c399459be82e50ef37ab203816
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279033"
---
# <a name="ltthreadgt-functions"></a>&lt;thread&gt;-Funktionen

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[swap](#swap)|[yield](#yield)|

## <a name="get_id"></a> get_id

Weist den aktuellen Ausführungsthread eindeutig aus.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ [Thread:: ID](../standard-library/thread-class.md), das den aktuellen Ausführungsthread eindeutig ausweist.

## <a name="sleep_for"></a> sleep_for

Blockiert den aufrufenden Thread.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parameter

*Rel_time*<br/>
Ein [Dauer](../standard-library/duration-class.md)-Objekt, das ein Zeitintervall angibt.

### <a name="remarks"></a>Hinweise

Die Funktion sperrt den aufrufenden Thread für mindestens die Zeit, die angegebenen *Rel_time*. Diese Funktion löst keine Ausnahmen aus.

## <a name="sleep_until"></a> sleep_until

Blockiert den aufrufenden Thread mindestens bis zum angegebenen Zeitpunkt.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parameter

*Abs_time*<br/>
Stellt einen Zeitpunkt dar.

### <a name="remarks"></a>Hinweise

Diese Funktion löst keine Ausnahmen aus.

## <a name="swap"></a>  swap

Vertauscht die Zustände von zwei **Thread** Objekte.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parameter

*Links*<br/>
Der linken Seite **Thread** Objekt.

*Rechts*<br/>
Das Recht **Thread** Objekt.

### <a name="remarks"></a>Hinweise

Die Funktion ruft `Left.swap(Right)` auf.

## <a name="yield"></a> yield

Signalisiert dem Betriebssystem, andere Threads auszuführen, auch wenn der aktuelle Thread normalerweise weiterhin ausgeführt werden würde.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Siehe auch

[\<thread>](../standard-library/thread.md)<br/>
