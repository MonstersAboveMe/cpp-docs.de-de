---
title: Compilerfehler C3717
ms.date: 11/04/2016
f1_keywords:
- C3717
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
ms.openlocfilehash: f7e60b4f1b6a1337ef93088e4f36ce2a1b34dc47
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328275"
---
# <a name="compiler-error-c3717"></a>Compilerfehler C3717

"Method": eine Methode, die Ereignisse auslöst, kann nicht definiert werden

Sie haben eine Ereignismethode, die die Implementierung umfasst deklariert. Ein [__event](../../cpp/event.md) Deklaration der Methode kann keine Definition haben. Um diesen Fehler zu beheben, stellen Sie sicher, dass keine Methode Ereignisdeklarationen Definitionen verfügen. Z. B. in den folgenden Code entfernen den Hauptteil der Funktion aus der `event1` Deklaration wie durch den Kommentaren angegeben.

Im folgende Beispiel wird die C3717 generiert:

```
// C3717.cpp
[event_source(native)]
class CEventSrc {
public:
   __event void event1() {   // C3717
   }

   // remove definition for event1 and substitute following declaration
   // __event void event1();
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