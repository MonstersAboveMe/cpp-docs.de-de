---
title: Compilerwarnung (Stufe 1) C4376
ms.date: 11/04/2016
f1_keywords:
- C4376
helpviewer_keywords:
- C4376
ms.assetid: 5f202c74-9489-48fe-b36f-19cd882b1589
ms.openlocfilehash: b1f6e7b403931f7fe1a67974ae85001cf80eab66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410433"
---
# <a name="compiler-warning-level-1-c4376"></a>Compilerwarnung (Stufe 1) C4376

Zugriffsspezifizierer 'old_specifier:' wird nicht mehr unterstützt: Verwenden Sie stattdessen 'new_specifier:'

Weitere Informationen zum Angeben von Typen und Member in Metadaten finden Sie unter [geben Sichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) und [membersichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility) in [Vorgehensweise: Definieren und Verarbeiten von Klassen und Strukturen (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Beispiel

Im folgende Beispiel wird C4376 generiert.

```
// C4376.cpp
// compile with: /clr /W1 /c
public ref class G {
public public:   // C4376
   void m2();
};

public ref class H {
public:   // OK
   void m2();
};
```