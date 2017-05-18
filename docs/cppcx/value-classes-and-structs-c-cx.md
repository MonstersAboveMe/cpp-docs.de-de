---
title: "Wertklassen und Strukturen (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "value struct"
  - "value class"
ms.assetid: 262a0992-9721-4c02-8297-efc07d90e5a4
caps.latest.revision: 12
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 12
---
# Wertklassen und Strukturen (C++/CX)
Eine *Wertstruktur* oder *Wertklasse* ist [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]\-kompatible POD \(Plain Old Data structure\). Sie verfügt über eine feste Größe und besteht nur aus Feldern. Anders als eine Verweisklasse hat sie keine Eigenschaften.  
  
 Die folgenden Beispiele zeigen, wie Wertstrukturen deklariert und initialisiert werden.  
  
```  
  
// in mainpage.xaml.h: value struct TestStruct { Platform::String^ str; int i; }; value struct TestStruct2 { TestStruct ts; Platform::String^ str; int i; }; // in mainpage.cpp: // Initialize a value struct with an int and String TestStruct ts = {"I am a TestStruct", 1}; // Initialize a value struct that contains // another value struct, an int and a String TestStruct2 ts2 = {{"I am a TestStruct", 1}, "I am a TestStruct2", 2}; // Initialize value struct members individually. TestStruct ts3; ts3.i = 108; ts3.str = "Another way to init a value struct.";  
  
```  
  
 Wenn eine Variable eines Werttyps einer anderen Variablen zugewiesen wird, wird der Wert kopiert, damit jede der beiden Variablen eine eigene Kopie der Daten besitzt. Eine *Wertstruktur* ist eine Struktur fester Größe, die nur öffentliche Datenfelder enthält und durch das Schlüsselwort `value struct` deklariert wird.  
  
 Eine *Wertklasse* entspricht `value struct`, außer dass den zugehörigen Felder explizit öffentliche Zugreifbarkeit zugeordnet werden muss. Sie wird durch das Schlüsselwort `value class` deklariert.  
  
 Eine Wertstruktur oder Wertklasse kann als Felder nur grundlegende numerische Typen, Enumerationsklassen, `Platform::String^` oder [Platform::IBox \<T\>^](../cppcx/platform-ibox-interface.md) enthalten, wobei T eine Klasse vom Typ numerisch oder eine Enumerationsklasse oder eine Wertklasse oder eine Struktur ist. Ein `IBox<T>^`\-Feld kann den Wert `nullptr` haben. Auf diese Weise implementiert C\+\+ das Konzept der auf *NULL festlegbaren Werttypen*.  
  
 Eine Wertklasse oder Wertstruktur, die einen `Platform::String^`\- oder `IBox<T>^`\-Typ als Member enthält, das nicht `memcpy`\-fähig ist.  
  
 Da alle Member einer `value class` oder `value struct` öffentlich sind und in Metadaten ausgegeben werden, sind C\+\+\-Standardtypen als Member nicht zulässig. Dies unterscheidet sich von Verweisklassen, die `private` oder `internal` C\+\+\-Standardtypen enthalten können.  
  
 Im folgenden Codefragment werden die `Coordinates`\- und `City`\-Typen als Wertstrukturen deklariert. Beachten Sie, dass einer der `City`\-Datenmember ein `GeoCoordinates`\-Typ ist. Eine `value struct` kann andere Wertstrukturen als Member enthalten.  
  
 [!code-cpp[cx_classes#07](../snippets/cpp/VS_Snippets_Misc/cx_classes/cpp/class1.h#07)]  
  
## Parameterübergabe für Werttypen  
 Wenn Sie über einen Werttyp als Funktions\- oder Methodenparameter verfügen, wird er normalerweise als Wert übergeben. Bei größeren Objekten kann dies zu Leistungsproblemen führen. In Visual Studio 2013 und früher werden Werttypen in C\+\+\/CX immer als Wert übergeben. In Visual Studio 2015 und höher können Werttypen als Verweis oder als Wert übergeben werden.  
  
 Verwenden Sie zum Deklarieren eines Parameters, der einen Werttyp als Wert übergibt, Code wie den folgenden:  
  
```  
void Method1(MyValueType obj);  
```  
  
 Um einen Parameter zu deklarieren, der einen Werttyp als Verweis übergibt, verwenden Sie das Verweissymbol \(&\), wie im Folgenden dargestellt:  
  
```  
void Method2(MyValueType& obj);  
```  
  
 Der Typ in „Method2“ ist ein Verweis auf „MyValueType“ und funktioniert in der gleichen Weise wie ein Verweistyp in standardmäßigem C\+\+.  
  
 Wenn Sie „Method1“ von einer anderen Sprache, wie etwa C\#, aus aufrufen, brauchen Sie das Schlüsselwort `ref` oder `out` nicht zu verwenden. Wenn Sie „Method2“ aufrufen, verwenden Sie das `ref`\-Schlüsselwort.  
  
```  
Method2(ref obj);  
```  
  
 Sie können auch ein Zeigersymbol \(\*\) verwenden, um einen Werttyp als Verweis zu übergeben. Das Verhalten in Bezug auf Aufrufer in anderen Sprachen ist identisch \(Aufrufer in C\# verwenden das `ref`\-Schlüsselwort \), aber in der Methode ist der Typ ein Zeiger auf den Werttyp.  
  
## Auf NULL festlegbare Werttypen  
 Wie bereits erwähnt, können eine Wertklasse oder eine Wertstruktur ein Feld des Typs [Platform::IBox\<T\>^](../cppcx/platform-ibox-interface.md) aufweisen, z. B. `IBox<int>^`. Ein solches Feld kann jeden beliebigen numerischen Wert haben, der für den Typ `int` gültig ist, oder er kann den Wert `nullptr` haben. Sie können ein auf NULL festlegbares Feld als Argument an eine Methode, deren Parameter als optional deklariert ist, oder an eine beliebige andere Stelle übergeben, für die ein Werttyp keinen Wert haben muss.  
  
 Im folgenden Beispiel wird veranschaulicht, wie eine Struktur mit einem auf NULL festlegbaren Feld initialisiert wird.  
  
```  
public value struct Student { Platform::String^ Name; int EnrollmentYear; Platform::IBox<int>^ GraduationYear; // Null if not yet graduated. }; //To create a Student struct, one must populate the nullable type. MainPage::MainPage() { InitializeComponent(); Student A; A.Name = "Alice"; A.EnrollmentYear = 2008; A.GraduationYear = ref new Platform::Box<int>(2012); Student B; B.Name = "Bob"; B.EnrollmentYear = 2011; B.GraduationYear = nullptr; IsCurrentlyEnrolled(A); IsCurrentlyEnrolled(B); } bool MainPage::IsCurrentlyEnrolled(Student s) { if (s.GraduationYear == nullptr) { return true; } return false; }  
  
```  
  
 Eine Wertstruktur selbst kann genauso auf NULL festgelegt werden, wie hier dargestellt:  
  
```  
  
public value struct MyStruct { public: int i; Platform::String^ s; }; public ref class MyClass sealed { public: property Platform::IBox<MyStruct>^ myNullableStruct; };  
```  
  
## Siehe auch  
 [Typsystem \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Sprachreferenz zu Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Namespaceverweis](../cppcx/namespaces-reference-c-cx.md)   
 [Verweisklassen und Strukturen \(C\+\+\/CX\)](../cppcx/ref-classes-and-structs-c-cx.md)