---
title: Compilerfehler C3724
ms.date: 11/04/2016
f1_keywords:
- C3724
helpviewer_keywords:
- C3724
ms.assetid: cab8aba7-14fc-406f-8cc6-32744c8f31c1
ms.openlocfilehash: 126317d78785b14f5ef613ec0c83d3e50b825d60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328158"
---
# <a name="compiler-error-c3724"></a>Compilerfehler C3724

muss #include \<windows.h > Verwendung von Multithreading mit Ereignissen

Datei windows.h ist erforderlich, bei Verwendung von Multithreading mit Ereignissen. Um diesen Fehler zu beheben, fügen `#include <windows.h>` am Anfang der Datei in der Ereignisquelle und Empfänger definiert sind.

```
// C3724.cpp
// uncomment the following line to resolve
// #include <windows.h>

[event_source(native), threading(apartment)]
class CEventSrc {
public:
   __event void event1();   // C3724
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
   }

   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```