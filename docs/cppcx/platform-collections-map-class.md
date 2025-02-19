---
title: Platform::Collections::Map-Klasse
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::Map::Map
- COLLECTION/Platform::Collections::Map::Clear
- COLLECTION/Platform::Collections::Map::First
- COLLECTION/Platform::Collections::Map::GetView
- COLLECTION/Platform::Collections::Map::HasKey
- COLLECTION/Platform::Collections::Map::Insert
- COLLECTION/Platform::Collections::Map::Lookup
- COLLECTION/Platform::Collections::Map::Remove
- COLLECTION/Platform::Collections::Map::Size
helpviewer_keywords:
- Map Class (C++/Cx)
ms.assetid: 2b8cf968-1167-4898-a149-1195b32c1785
ms.openlocfilehash: ce50290217c7c06e26f26fc50564d3e37c873157
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161757"
---
# <a name="platformcollectionsmap-class"></a>Platform::Collections::Map-Klasse

Stellt eine *Zuordnung*dar, die eine Auflistung von Schlüssel-Wert-Paaren ist.

## <a name="syntax"></a>Syntax

```cpp
template <
   typename K,
   typename V,
   typename C = std::less<K>>
ref class Map sealed;
```

### <a name="parameters"></a>Parameter

*K*<br/>
Der Typ des Schlüssels im Schlüssel-Wert-Paar.

*V*<br/>
Der Typ des Werts im Schlüssel-Wert-Paar.

*C*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen. In der Standardeinstellung [Std:: less\<K >](../standard-library/less-struct.md).

*__is_valid_winrt_type()* eine vom Compiler generierte Funktion, die überprüft, den Typ des ob *K* und *V* und bietet eine benutzerfreundliche Fehlermeldung, wenn der Typ in der Zuordnung gespeichert werden kann.

### <a name="remarks"></a>Hinweise

Zulässige Typen sind:

- Ganze Zahlen

- Schnittstellenklasse ^

- Öffentliche Referenzklasse^

- value struct

- Öffentliche Enumerationsklasse

Die Zuordnung ist im Grunde genommen ein Wrapper für [std::map](../standard-library/map-class.md). Es ist eine konkrete C++-Implementierung, der die [Windows::Foundation::Collections::IMap < Windows::Foundation::Collections::IKeyValuePair\<K, V >>](/uwp/api/Windows.Foundation.Collections.IMap_K_V_) und [IObservableMap](/uwp/api/Windows.Foundation.Collections.IObservableMap_K_V_) Windows-Runtime-Schnittstellen Typen, die über öffentliche übergeben werden. Wenn Sie versuchen, einen `Platform::Collections::Map` -Typ in einem öffentlichen Rückgabewert oder Parameter zu verwenden, wird der Compilerfehler C3986 ausgelöst. Sie können den Fehler beheben, ändern Sie den Typ des Parameters oder des Rückgabewerts Werts, der [Windows::Foundation::Collections::IMap\<K, V >](/uwp/api/Windows.Foundation.Collections.IMap_K_V_).

Weitere Informationen finden Sie unter [Sammlungen](../cppcx/collections-c-cx.md).

### <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Map::Map](#ctor)|Initialisiert eine neue Instanz der Map-Klasse.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[Map::Clear](#clear)|Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.|
|[Map:: First](#first)|Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt.|
|[Map::GetView](#getview)|Gibt eine schreibgeschützte Ansicht der aktuellen Zuordnung zurück; das heißt, eine [Platform::Collections::MapView Class](../cppcx/platform-collections-mapview-class.md).|
|[Map::HasKey](#haskey)|Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.|
|[Map::Insert](#insert)|Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.|
|[Map::Lookup](#lookup)|Ruft das Element am angegebenen Schlüssel im aktuellen Map-Objekt ab.|
|[Map::Remove](#remove)|Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.|
|[Map::Size](#size)|Gibt die Anzahl von Elementen im aktuellen Map-Objekt zurück.|

### <a name="events"></a>Ereignisse

|||
|-|-|
|name|Beschreibung|
|[Map:: mapchanged](#mapchanged) Ereignis|Tritt auf, wenn sich die Map ändert.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Map`

### <a name="requirements"></a>Anforderungen

**Header:** collection.h

**Namespace:** Platform::Collections

## <a name="clear"></a>  Map:: Clear-Methode

Entfernt alle Schlüssel-Wert-Paare aus dem derzeitigen Map-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Clear();
```

## <a name="first"></a>  Map:: First-Methode

Gibt einen Iterator zurück, der das erste Element in der Zuordnung angibt, oder `nullptr`, wenn die Zuordnung leer ist.

### <a name="syntax"></a>Syntax

```cpp
virtual Windows::Foundation::Collections::IIterator<
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();
```

### <a name="return-value"></a>Rückgabewert

Ein Iterator, der das erste Element in der Zuordnung angibt.

### <a name="remarks"></a>Hinweise

Den Rückgabewert einer Variablen zuweisen, die mit deklariert ist eine bequeme Möglichkeit, den von First() zurückgegeben Iterator zu halten ist die **automatisch** typableitungs-Schlüsselwort. Beispielsweise `auto x = myMap->First();`.

## <a name="getview"></a>  Map:: GetView-Methode

Gibt eine schreibgeschützte Ansicht der aktuellen Zuordnung zurück; d. h. eine [Platform::Collections::MapView Klasse](../cppcx/platform-collections-mapview-class.md), implementiert der [Windows::Foundation::Collections::IMapView\<K, V >] / uwp/api/Windows.Foundation.Collections.IMapView_K_V_) Schnittstelle.

### <a name="syntax"></a>Syntax

```cpp
Windows::Foundation::Collections::IMapView<K, V>^ GetView();
```

### <a name="return-value"></a>Rückgabewert

Ein `MapView`-Objekt.

## <a name="haskey"></a>  Map:: haskey-Methode

Ermittelt, ob die aktuelle Map den angegebenen Schlüssel enthält.

### <a name="syntax"></a>Syntax

```cpp
bool HasKey(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen des Map-Elements verwendete Schlüssel. Der Typ des *Schlüssel* ist der Typname *K*.

### <a name="return-value"></a>Rückgabewert

**"true"** ist der Schlüssel gefunden wird; andernfalls **"false"**.

## <a name="insert"></a>  Map:: Insert-Methode

Fügt das angegebene Schlüssel-Wert-Paar dem aktuellen Map-Objekt hinzu.

### <a name="syntax"></a>Syntax

```cpp
virtual bool Insert(K key, V value);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der Typ des *Schlüssel* ist der Typname *K*.

*value*<br/>
Der Wertteil des Schlüssel-Wert-Paars. Der Typ des *Wert* ist der Typname *V*.

### <a name="return-value"></a>Rückgabewert

**"true"** Wenn der Schlüssel eines vorhandenen Elements in der aktuellen Zuordnung entspricht *Schlüssel* und der Wertteil dieses Elements auf *Wert*. **"false"** kein vorhandenes Element in der aktuellen Zuordnung übereinstimmt *Schlüssel* und *Schlüssel* und *Wert* Parametern zu einem Schlüssel-Wert-Paar gemacht und dann hinzugefügt werden die aktuelle Zuordnung.

## <a name="lookup"></a>  Map:: Lookup-Methode

Ruft den Wert des Typs V ab, der mit dem angegebenen Schlüssel des Typs K verknüpft ist, sofern der Schlüssel vorhanden ist.

### <a name="syntax"></a>Syntax

```cpp
V Lookup(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zum Suchen eines in der Zuordnung vorhandenen Elements verwendete Schlüssel. Der Typ des *Schlüssel* ist der Typname *K*.

### <a name="return-value"></a>Rückgabewert

Der Wert, der mit ein paar bildet die *Schlüssel*. Der Typ des Rückgabewerts ist der Typname *V*.

### <a name="remarks"></a>Hinweise

Wenn der Schlüssel nicht vorhanden ist, wird eine [Platform:: outofboundsexception](../cppcx/platform-outofboundsexception-class.md) ausgelöst.

## <a name="ctor"></a>  Map:: Map-Konstruktor

Initialisiert eine neue Instanz der Map-Klasse.

### <a name="syntax"></a>Syntax

```cpp
explicit Map(const C& comp = C());
explicit Map(const StdMap& m);
explicit Map(StdMap&& m ;
template <typename InIt>
Map(
   InItfirst,
   InItlast,
   const C& comp = C());
```

### <a name="parameters"></a>Parameter

*InIt*<br/>
Der Typname der aktuellen Map.

*comp*<br/>
Ein Typ, der ein Funktionsobjekt bereitstellt, das zwei Elementwerte als Sortierschlüssel vergleichen kann, um deren relative Reihenfolge in der Map zu bestimmen.

*m*<br/>
Ein Verweis oder [Rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md) zu einem `map Class` , wird verwendet, um die aktuelle Map zu initialisieren.

*first*<br/>
Der Eingabeiterator des ersten Elements in einem Bereich von Elementen, die verwendet werden, um die aktuelle Map zu initialisieren.

*last*<br/>
Der Eingabeiterator des ersten Elements nach einem Bereich von Elementen, die verwendet werden, um die aktuelle Map zu initialisieren.

## <a name="mapchanged"></a>  Map:: mapchanged-Ereignis

Wird ausgelöst, wenn ein Element in eine Zuordnung eingefügt bzw. aus der Zuordnung entfernt wird.

### <a name="syntax"></a>Syntax

```cpp
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;
```

### <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein [MapChangedEventHandler\<K, V >](/uwp/api/windows.foundation.collections.mapchangedeventhandler) , enthält Informationen über das Objekt, das ausgelöst wird, das Ereignis, sowie die Art der entstandenen Änderung darstellt. Siehe auch [IMapChangedEventArgs\<K >](/uwp/api/Windows.Foundation.Collections.IMapChangedEventArgs_K_) und [CollectionChange-Enumeration](/uwp/api/windows.foundation.collections.collectionchange).

## <a name="net-framework-equivalent"></a>Entsprechung in .NET Framework

Windows-Runtime-apps, die C#-Visual Basic oder-Projekt IMap\<K, V > als IDictionary\<K, V >.

## <a name="remove"></a>  Map:: Remove-Methode

Löscht das angegebene Schlüssel-Wert-Paar vom aktuellen Map-Objekt.

### <a name="syntax"></a>Syntax

```cpp
virtual void Remove(K key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüsselteil des Schlüssel-Wert-Paars. Der Typ des *Schlüssel* ist der Typname *K*.

## <a name="size"></a>  Map:: size-Methode

Gibt die Anzahl der [Windows::Foundation::Collections::IKeyValuePair\<K, V >](/uwp/api/Windows.Foundation.Collections.IKeyValuePair_K_V_) Elementen in der Zuordnung.

### <a name="syntax"></a>Syntax

```cpp
virtual property unsigned int Size;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Elementen in der Zuordnung.

## <a name="see-also"></a>Siehe auch

[Plattform-Namespace](platform-namespace-c-cx.md)<br/>
[Erstellen von Windows-Runtime-Komponenten in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
