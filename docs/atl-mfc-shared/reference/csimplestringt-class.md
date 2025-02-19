---
title: CSimpleStringT-Klasse
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: 1ec28ed5b2f5428cabcf7570c7ac53904e9a64f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252633"
---
# <a name="csimplestringt-class"></a>CSimpleStringT-Klasse

Diese Klasse stellt eine `CSimpleStringT` Objekt.

## <a name="syntax"></a>Syntax

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parameter

*BaseType*<br/>
Der Zeichentyp der String-Klasse. Einer der folgenden Werte ist möglich:

- **Char** (für ANSI-Zeichenfolgen).

- **"wchar_t"** (für Unicode-Zeichenfolgen).

- TCHAR (nach ANSI- und Unicode-Zeichenfolgen).

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Ein Zeiger auf eine Konstante Zeichenfolge.|
|[CSimpleStringT::PXSTR](#pxstr)|Ein Zeiger auf eine Zeichenfolge.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Erstellt `CSimpleStringT` Objekte auf unterschiedliche Weise.|
|[CSimpleStringT::~CSimpleStringT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CSimpleStringT::Append](#append)|Fügt eine `CSimpleStringT` Objekt zu einem vorhandenen `CSimpleStringT` Objekt.|
|[CSimpleStringT::AppendChar](#appendchar)|Fügt ein Zeichen zu einem vorhandenen `CSimpleStringT` Objekt.|
|[CSimpleStringT::CopyChars](#copychars)|Kopiert ein oder mehrere Zeichen in eine andere Zeichenfolge an.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Kopiert von ein oder mehrere Zeichen in eine andere Zeichenfolge, die in der die Puffer, die sich überschneiden.|
|[CSimpleStringT::Empty](#empty)|Erzwingt, dass eine Zeichenfolge, die eine Länge von 0 (null) haben.|
|[CSimpleStringT::FreeExtra](#freeextra)|Gibt zusätzliche zuvor vom Zeichenfolgenobjekt belegten Arbeitsspeicher frei.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Ruft ab, die zugeordneten Zeitdauer eine `CSimpleStringT` Objekt.|
|[CSimpleStringT::GetAt](#getat)|Gibt das Zeichen an der angegebenen Position zurück.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Gibt einen Zeiger auf die Zeichen in einem `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Gibt einen Zeiger auf die Zeichen in einem `CSimpleStringT`, wird auf die angegebene Länge.|
|[CSimpleStringT::GetLength](#getlength)|Gibt die Anzahl der Zeichen in einem `CSimpleStringT` Objekt.|
|[CSimpleStringT::GetManager](#getmanager)|Ruft ab, der Speicher-Manager, der die `CSimpleStringT` Objekt.|
|[CSimpleStringT::GetString](#getstring)|Ruft die Zeichenfolge|
|[CSimpleStringT::IsEmpty](#isempty)|Tests, ob eine `CSimpleStringT` Objekt keine Zeichen enthält.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Deaktiviert die verweiszählung und schützt die Zeichenfolge im Puffer.|
|[CSimpleStringT::Preallocate](#preallocate)|Ordnet eine bestimmte Menge an Arbeitsspeicher für den Zeichenpuffer.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Gibt die Steuerung des vom zurückgegebenen Puffers frei `GetBuffer`.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Gibt die Steuerung des vom zurückgegebenen Puffers frei `GetBuffer`.|
|[CSimpleStringT::SetAt](#setat)|Legt ein Zeichen an der angegebenen Position fest.|
|[CSimpleStringT::SetManager](#setmanager)|Legt die Speicher-Manager von einem `CSimpleStringT` Objekt.|
|[CSimpleStringT::SetString](#setstring)|Legt die Zeichenfolge von einem `CSimpleStringT` Objekt.|
|[CSimpleStringT::StringLength](#stringlength)|Gibt die Anzahl der Zeichen in der angegebenen Zeichenfolge zurück.|
|[CSimpleStringT::Truncate](#truncate)|Schneidet die Zeichenfolge, die einer angegebenen Länge ab.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Ermöglicht die verweiszählung und die Zeichenfolge im Puffer frei.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Greift direkt in gespeicherten Zeichen auf eine `CSimpleStringT` Objekts als Zeichenfolge im C-Stil.|
|[CSimpleStringT::operator\[\]](#operator_at)|Gibt das Zeichen an der angegebenen Position zurück, Operator Ersetzung für `GetAt`.|
|[CSimpleStringT::operator +=](#operator_add_eq)|Verkettet eine neue Zeichenfolge am Ende einer vorhandenen Zeichenfolge.|
|[CSimpleStringT::operator =](#operator_eq)|Weist einen neuen Wert ein `CSimpleStringT` Objekt.|

### <a name="remarks"></a>Hinweise

`CSimpleStringT` ist die Basisklasse für die verschiedenen Zeichenfolgenklassen, die von Visual C++ unterstützt. Es bietet minimale Unterstützung für die Speicherverwaltung des String-Objekt und grundlegende pufferbearbeitung. Erweiterte Zeichenfolgenobjekten, finden Sie unter [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Anforderungen

**Header:** atlsimpstr.h

## <a name="append"></a> CSimpleStringT::Append

Fügt eine `CSimpleStringT` Objekt zu einem vorhandenen `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parameter

*strSrc*<br/>
Die `CSimpleStringT` Objekt angefügt werden soll.

*pszSrc*<br/>
Ein Zeiger auf eine Zeichenfolge, die mit den Zeichen angefügt werden soll.

*nLength*<br/>
Die Anzahl der anzufügenden Zeichen.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Anfügen einer vorhandenen `CSimpleStringT` Objekt in ein anderes `CSimpleStringT` Objekt.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a> CSimpleStringT::AppendChar

Fügt ein Zeichen zu einem vorhandenen `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parameter

*ch*<br/>
Das Zeichen angefügt werden soll

### <a name="remarks"></a>Hinweise

Mit dieser Funktion können Sie das angegebene Zeichen am Ende eines vorhandenen Anfügen `CSimpleStringT` Objekt.

##  <a name="copychars"></a> CSimpleStringT::CopyChars

Kopiert ein oder mehrere Zeichen zu einem `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parameter

*pchDest*<br/>
Ein Zeiger auf eine Zeichenfolge.

*pchSrc*<br/>
Ein Zeiger auf eine Zeichenfolge, die mit den Zeichen kopiert werden soll.

*nChars*<br/>
Die Anzahl der *PchSrc* zu kopierenden Zeichen.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Kopieren von Zeichen aus *PchSrc* auf die *PchDest* Zeichenfolge.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>  CSimpleStringT::CopyCharsOverlapped

Kopiert ein oder mehrere Zeichen zu einem `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parameter

*pchDest*<br/>
Ein Zeiger auf eine Zeichenfolge.

*pchSrc*<br/>
Ein Zeiger auf eine Zeichenfolge, die mit den Zeichen kopiert werden soll.

*nChars*<br/>
Die Anzahl der *PchSrc* zu kopierenden Zeichen.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Kopieren von Zeichen aus *PchSrc* auf die *PchDest* Zeichenfolge. Im Gegensatz zu `CopyChars`, `CopyCharsOverlapped` bietet eine sichere Methode für das Kopieren von Zeichen-Puffern, die möglicherweise überlappen.

### <a name="example"></a>Beispiel

Siehe das Beispiel für [CSimpleStringT::CopyChars](#copychars), oder der Quellcode für `CSimpleStringT::SetString` (befindet sich im atlsimpstr.h).

##  <a name="ctor"></a>  CSimpleStringT::CSimpleStringT

Erstellt ein `CSimpleStringT`-Objekt.

### <a name="syntax"></a>Syntax

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parameter

*strSrc*<br/>
Eine vorhandene `CSimpleStringT` Objekt, das in diese kopiert werden `CSimpleStringT` Objekt.

*pchSrc*<br/>
Ein Zeiger auf ein Array von Zeichen Länge *nLength*, kein Null-terminiert.

*pszSrc*<br/>
Eine mit Null endende Zeichenfolge, die in diese kopiert werden `CSimpleStringT` Objekt.

*nLength*<br/>
Die Anzahl der Zeichen im `pch`.

*pStringMgr*<br/>
Ein Zeiger auf den Speicher-Manager, der die `CSimpleStringT` Objekt. Weitere Informationen zu `IAtlStringMgr` und Speicherverwaltung für `CSimpleStringT`, finden Sie unter [Speicherverwaltung und CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Hinweise

Erstellt ein neues `CSimpleStringT`-Objekt. Da die Konstruktoren der Eingabedaten in den neuen zugeordneten Speicher kopieren, können Memory-Ausnahmen führen.

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Verwendung von `CSimpleStringT::CSimpleStringT` mithilfe der ATL **Typedef** `CSimpleString`. `CSimpleString` ist eine häufig verwendete Spezialisierung der Klassenvorlage `CSimpleStringT`.

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

##  <a name="empty"></a>  CSimpleStringT::Empty

Dadurch `CSimpleStringT` Objekt eine leere Zeichenfolge und gibt den Arbeitsspeicher nach Bedarf frei.

### <a name="syntax"></a>Syntax

```
void Empty() throw();
```

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [Zeichenfolgen: CString-Ausnahmebereinigung](../cstring-exception-cleanup.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>  CSimpleStringT::FreeExtra

Gibt frei, zusätzlichen Arbeitsspeicher, der zuvor von der Zeichenfolge zugeordnet, aber nicht mehr benötigt.

### <a name="syntax"></a>Syntax

```
void FreeExtra();
```

### <a name="remarks"></a>Hinweise

Dies sollte den Speicher-Overhead, der vom Zeichenfolgenobjekt verbraucht reduzieren. Die Methode zuordnet, den Puffer, die genaue Länge zurückgegebenes [GetLength](#getlength).

### <a name="example"></a>Beispiel

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>Hinweise

In diesem Beispiel wird die Ausgabe lautet wie folgt aus:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

##  <a name="getalloclength"></a>  CSimpleStringT::GetAllocLength

Ruft ab, die zugeordneten Zeitdauer eine `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen, die diesem Objekt zugeordnet.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Ermitteln der Anzahl von Zeichen, die für diese zugeordneten `CSimpleStringT` Objekt. Finden Sie unter [FreeExtra](#freeextra) ein Beispiel für das Aufrufen dieser Funktion.

##  <a name="getat"></a>  CSimpleStringT::GetAt

Gibt ein Zeichen aus einer `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierte Index des Zeichens in der `CSimpleStringT` Objekt. Die *iChar* Parameter muss größer als oder gleich 0 und kleiner als der Rückgabewert von [GetLength](#getlength). Andernfalls `GetAt` wird eine Ausnahme generiert.

### <a name="return-value"></a>Rückgabewert

Ein `XCHAR` , enthält das Zeichen an der angegebenen Position in der Zeichenfolge.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um zurückzugeben, die ein Zeichen, die anhand des *iChar*. Der überladene Feldindex (**[]**)-Operator ist ein zweckmäßiger Alias für `GetAt`. Der null-Terminator ist adressierbar, ohne Auslösen einer Ausnahme mit `GetAt`. Es wird jedoch nicht gezählt von `GetLength`, und der zurückgegebene Wert ist 0.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>  CSimpleStringT::GetBuffer

Gibt einen Zeiger auf den internen Zeichenpuffer für den `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parameter

*nMinBufferLength*<br/>
Die minimale Anzahl von Zeichen, die der Zeichenpuffer enthalten kann. Dieser Wert umfasst nicht den verbliebenen Speicherplatz für einen null-Terminator.

Wenn *nMinBufferLength* ist größer als die Länge des aktuellen Puffers `GetBuffer` des aktuellen Puffers löscht, ersetzt diese durch einen Puffer mit der angeforderten Größe und den Verweiszähler des Objekts auf 0 (null) zurückgesetzt. Wenn Sie bereits zuvor aufgerufen haben [LockBuffer](#lockbuffer) diesen Puffer, verlieren Sie die Sperre des Puffers.

### <a name="return-value"></a>Rückgabewert

Ein `PXSTR` Zeiger auf die (Null) endende Puffer des Objekts.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Zurückgeben von den Inhalt des Puffers, der die `CSimpleStringT` Objekt. Das zurückgegebene `PXSTR` ist keine Konstante und aus diesem Grund können direkte Änderung von `CSimpleStringT` Inhalt.

Bei Verwendung den vom Zeiger `GetBuffer` um den Inhalt der Zeichenfolge zu ändern, rufen Sie [ReleaseBuffer](#releasebuffer) vor der Verwendung von anderen `CSimpleStringT` Membermethoden.

Die Adresse, die vom `GetBuffer` möglicherweise aufgrund ungültiger nach dem Aufruf von `ReleaseBuffer` da zusätzliche `CSimpleStringT` Vorgänge können dazu führen, dass die `CSimpleStringT` Puffer, verschoben werden. Der Puffer ist nicht neu zugeordnet, wenn Sie nicht die Länge des Ändern der `CSimpleStringT`.

Der Arbeitsspeicherpuffer wird automatisch freigegeben wird, wenn die `CSimpleStringT` -Objekt zerstört wird.

Wenn Sie die Länge der Zeichenfolge selbst mitverfolgen, sollten Sie nicht das abschließende Nullzeichen anhängen. Allerdings müssen Sie die endgültige Zeichenfolgenlänge angeben, wenn Sie den Puffer mit freigeben `ReleaseBuffer`. Wenn Sie ein abschließendes Nullzeichen anfügen, sollten Sie-1 (Standardwert) für die Länge übergeben. `ReleaseBuffer` Klicken Sie dann bestimmt die Länge des Puffers.

Es ist nicht genügend Arbeitsspeicher zum Erfüllen der `GetBuffer` anfordern, diese Methode löst eine CMemoryException *.

### <a name="example"></a>Beispiel

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

##  <a name="getbuffersetlength"></a>  CSimpleStringT::GetBufferSetLength

Gibt einen Zeiger auf den internen Zeichenpuffer für den `CSimpleStringT` Objekt abschneiden oder seine Länge wächst, bei Bedarf exakt in festgelegte Länge *nLength*.

### <a name="syntax"></a>Syntax

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parameter

*nLength*<br/>
Die genaue Größe der dem `CSimpleStringT` Zeichen-Puffers in Zeichen.

### <a name="return-value"></a>Rückgabewert

Ein `PXSTR` Zeiger auf die (Null) endende Puffer des Objekts.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Abrufen von einer angegebenen Länge des internen Puffers der `CSimpleStringT` Objekt. Das zurückgegebene `PXSTR` Zeiger ist nicht **const** und auf diese Weise direkte Änderung von `CSimpleStringT` Inhalt.

Bei Verwendung den vom Zeiger [GetBufferSetLength](#getbuffersetlength) aufrufen, um den Inhalt der Zeichenfolge zu ändern, `ReleaseBuffer` zum Aktualisieren des internen Zustands des `CsimpleStringT` vor der Verwendung von anderen `CSimpleStringT` Methoden.

Die Adresse, die vom `GetBufferSetLength` möglicherweise aufgrund ungültiger nach dem Aufruf von `ReleaseBuffer` da zusätzliche `CSimpleStringT` Vorgänge können dazu führen, dass die `CSimpleStringT` Puffer, verschoben werden. Der Puffer ist nicht neu zugewiesen, wenn Sie nicht die Länge des Ändern der `CSimpleStringT`.

Der Arbeitsspeicherpuffer wird automatisch freigegeben wird, wenn die `CSimpleStringT` -Objekt zerstört wird.

Wenn Sie die Länge der Zeichenfolge selbst mitverfolgen, fügen Sie das abschließende Nullzeichen nicht. Sie müssen die endgültige Zeichenfolgenlänge angeben, wenn Sie mit den Puffer freigibt `ReleaseBuffer`. Wenn Sie ein abschließendes Nullzeichen beim Aufrufen Anfügen `ReleaseBuffer`, übergeben Sie – 1 (Standard) für die Dauer zum `ReleaseBuffer`, und `ReleaseBuffer` führt eine `strlen` im Puffer, um zu bestimmen, seine Länge.

Weitere Informationen zum zählen der Verweise finden Sie unter den folgenden Artikeln:

- [Verwalten der Lebensdauer von Objekten über die Verweiszählung](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) in das Windows SDK.

- [Implementieren die Verweiszählung](/windows/desktop/com/implementing-reference-counting) in das Windows SDK.

- [Regeln für die Verwaltung von Verweiszähler](/windows/desktop/com/rules-for-managing-reference-counts) in das Windows SDK.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::GetBufferSetLength`.

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

##  <a name="getlength"></a>  CSimpleStringT::GetLength

Gibt die Anzahl der Zeichen in der `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
int GetLength() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen in der Zeichenfolge.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um die Anzahl der Zeichen im Objekt zurück. Die Anzahl die enthält einen null-Terminator keine.

Für multibyte-Zeichensätze (MBCS), setzt `GetLength` Anzahl jedes 8-Bit-Zeichen, d. h. ein und die nachfolgenden Byte in einer Multibyte-Zeichen werden als zwei Bytes gezählt. Finden Sie unter [FreeExtra](#freeextra) ein Beispiel für das Aufrufen dieser Funktion.

##  <a name="getmanager"></a>  CSimpleStringT::GetManager

Ruft ab, der Speicher-Manager, der die `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Speicher-Manager für die `CSimpleStringT` Objekt.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Abrufen des Speichers-Manager verwendet werden, indem die `CSimpleStringT` Objekt. Weitere Informationen zu Speicher-Manager und String-Objekten, finden Sie unter [Speicherverwaltung und CStringT](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>  CSimpleStringT::GetString

Ruft die Zeichenfolge ab.

### <a name="syntax"></a>Syntax

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Null-terminierte Zeichenfolge.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um die zugeordnete Zeichenfolge abgerufen werden. die `CSimpleStringT` Objekt.

> [!NOTE]
>  Das zurückgegebene `PCXSTR` Zeiger **const** und lässt keine direkte Änderung von `CSimpleStringT` Inhalt.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>  CSimpleStringT::IsEmpty

Tests eine `CSimpleStringT` -Objekt für die leere Bedingung.

### <a name="syntax"></a>Syntax

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt "true" zurück, wenn die `CSimpleStringT` Objekt verfügt über 0 Länge; andernfalls "false".

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um zu bestimmen, ob das Objekt eine leere Zeichenfolge enthält.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>  CSimpleStringT::LockBuffer

Deaktiviert die verweiszählung und schützt die Zeichenfolge im Puffer.

### <a name="syntax"></a>Syntax

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine `CSimpleStringT` Objekt oder ein Null-terminierte Zeichenfolge.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Sperren des Puffers, der die `CSimpleStringT` Objekt. Durch Aufrufen von `LockBuffer`, Sie erstellen eine Kopie der Zeichenfolge durch-1 für den Verweiszähler. Wenn die Verweisanzahl den Wert-1 ist, gilt die Zeichenfolge im Puffer "gesperrt" sein. Während im gesperrten Zustand, wird die Zeichenfolge auf zwei Arten geschützt:

- Keine andere Zeichenfolge erhalten einen Verweis auf die Daten in der Zeichenfolge gesperrt, auch wenn diese Zeichenfolge auf die gesperrte Zeichenfolge zugeordnet ist.

- Die gesperrte Zeichenfolge wird nie einer anderen Zeichenfolge und verweisen, auch wenn diese andere Zeichenfolge an die gesperrten Zeichenfolge kopiert wird.

Sperren die Zeichenfolge im Puffer, stellen Sie sicher, dass der Zeichenfolge exklusive Sperre des Puffers intakt bleiben.

Wenn Sie fertig sind `LockBuffer`, rufen Sie [UnlockBuffer](#unlockbuffer) den Verweiszähler auf 1 zurückgesetzt.

> [!NOTE]
>  Aufrufen [GetBuffer](#getbuffer) auf einen Puffer gesperrt, und Sie legen die `GetBuffer` Parameter `nMinBufferLength` auf einen Wert größer als die Länge des aktuellen Puffers, verlieren Sie die Sperre des Puffers. Solch ein Aufruf zum `GetBuffer` des aktuellen Puffers löscht, ersetzt es durch einen Puffer mit der angeforderten Größe und den Verweiszähler auf 0 (null) zurückgesetzt.

Weitere Informationen zum zählen der Verweise finden Sie unter den folgenden Artikeln:

- [Verwalten der Lebensdauer von Objekten über die Verweiszählung](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) in das Windows SDK

- [Implementieren die Verweiszählung](/windows/desktop/com/implementing-reference-counting) in das Windows SDK

- [Regeln für die Verwaltung von Verweiszähler](/windows/desktop/com/rules-for-managing-reference-counts) in das Windows SDK

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

##  <a name="operator_at"></a>  CSimpleStringT::operator\[\]

Rufen Sie diese Funktion für den Zugriff auf ein einzelnes Zeichen, die Arrays von Zeichen an.

### <a name="syntax"></a>Syntax

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierte Index eines Zeichens in der Zeichenfolge.

### <a name="remarks"></a>Hinweise

Der überladene Feldindex (**[]**) Operator gibt ein einzelnes Zeichen, die über den nullbasierten Index im angegebenen *iChar*. Dieser Operator ist, einen geeigneten Ersatz für die [GetAt](#getat) Member-Funktion.

> [!NOTE]
>  Können Sie der Feldindex (**[]**) Operator, um den Wert eines Zeichens in einer `CSimpleStringT`, aber Sie können nicht zum Ändern des Werts eines Zeichens in einer `CSimpleStringT`.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>  CSimpleStringT::operator \[\]

Rufen Sie diese Funktion für den Zugriff auf ein einzelnes Zeichen, die Arrays von Zeichen an.

### <a name="syntax"></a>Syntax

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierte Index eines Zeichens in der Zeichenfolge.

### <a name="remarks"></a>Hinweise

Der überladene Feldindex (**[]**) Operator gibt ein einzelnes Zeichen, die über den nullbasierten Index im angegebenen *iChar*. Dieser Operator ist, einen geeigneten Ersatz für die [GetAt](#getat) Member-Funktion.

> [!NOTE]
>  Können Sie der Feldindex (**[]**) Operator, um den Wert eines Zeichens in einer `CSimpleStringT`, aber Sie können nicht zum Ändern des Werts eines Zeichens in einer `CSimpleStringT`.

##  <a name="operator_add_eq"></a>  CSimpleStringT::operator +=

Verknüpft eine neue Zeichenfolge oder das Zeichen am Ende einer vorhandenen Zeichenfolge an.

### <a name="syntax"></a>Syntax

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Ein Zeiger auf eine Null-terminierte Zeichenfolge.

*strSrc*<br/>
Ein Zeiger auf eine vorhandene `CSimpleStringT` Objekt.

*ch*<br/>
Das Zeichen, das angefügt werden soll.

### <a name="remarks"></a>Hinweise

Der Operator akzeptiert eine andere `CSimpleStringT` Objekt oder ein Zeichen. Beachten Sie, dass der Speicher Ausnahmen auftreten, wenn dieser Operator für zeichenfolgenverkettung verwenden, da für Zeichen, die hinzugefügt wurde mit neuer Speicher zugeordnet werden kann `CSimpleStringT` Objekt.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>  CSimpleStringT::operator =

Weist einen neuen Wert ein `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Ein Zeiger auf eine Null-terminierte Zeichenfolge.

*strSrc*<br/>
Ein Zeiger auf eine vorhandene `CSimpleStringT` Objekt.

### <a name="remarks"></a>Hinweise

Wenn die Zielzeichenfolge (links) bereits vorhanden sind, die zum Speichern der neuen Daten groß genug ist, wird keine neue speicherbelegung ausgeführt. Beachten Sie, dass der Speicher Ausnahmen auftreten, wenn Sie den Zuweisungsoperator verwenden, da häufig mit neuer Speicher, zum Speichern der resultierenden zugeordnet wird `CSimpleStringT` Objekt.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator =`.

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

##  <a name="operator_pcxstr"></a>  CSimpleStringT::operator PCXSTR

Greift direkt in gespeicherten Zeichen auf eine `CSimpleStringT` Objekts als Zeichenfolge im C-Stil.

### <a name="syntax"></a>Syntax

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeichenzeiger auf Daten von der Zeichenfolge.

### <a name="remarks"></a>Hinweise

Es werden keine Zeichen kopiert werden. nur ein Zeiger zurückgegeben. Achten Sie darauf, dass mit diesem Operator. Wenn Sie ändern eine `CString` Objekt nach dem Sie die Zeichenzeiger erhalten haben, verursachen Sie vielleicht einer neuzuordnung von Arbeitsspeicher, der den Zeiger ungültig.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::operator PCXSTR`.

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

##  <a name="pcxstr"></a>  CSimpleStringT::PCXSTR

Ein Zeiger auf eine Konstante Zeichenfolge.

### <a name="syntax"></a>Syntax

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>  CSimpleStringT::Preallocate

Belegt eine bestimmte Menge an Bytes für den `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parameter

*nLength*<br/>
Die genaue Größe der dem `CSimpleStringT` Zeichen-Puffers in Zeichen.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um eine bestimmte Puffergröße für Zuordnen der `CSimpleStringT` Objekt.

`CSimpleStringT` wird eine STATUS_NO_MEMORY-Ausnahme generiert, wenn sie den Zeichenpuffer Speicher zugewiesen werden kann. Standardmäßig erfolgt die speicherbelegung von Win32-API-Funktionen `HeapAlloc` oder `HeapReAlloc`.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>  CSimpleStringT::PXSTR

Ein Zeiger auf eine Zeichenfolge.

### <a name="syntax"></a>Syntax

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>  CSimpleStringT::ReleaseBuffer

Gibt die Steuerung des vom reservierten Puffers frei [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntax

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parameter

*nNewLength*<br/>
Die neue Länge der Zeichenfolge in Zeichen, die einen null-Terminator wird dabei nicht mitgezählt. Der Standardwert-1 legt fest, wenn die Zeichenfolge null-termininiert ist, die `CSimpleStringT` Größe auf die aktuelle Länge der Zeichenfolge.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um zum erneuten zuweisen, oder geben Sie den Puffer mit String-Objekt frei. Wenn Sie wissen, dass die Zeichenfolge im Puffer Null-terminiert ist, können Sie weglassen der *nNewLength* Argument. Wenn die Zeichenfolge ungleich null beendet ist, verwenden Sie *nNewLength* seine Länge an. Die Adresse, die vom [GetBuffer](#getbuffer) ist ungültig. nach dem Aufruf von `ReleaseBuffer` oder einen anderen `CSimpleStringT` Vorgang.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::ReleaseBuffer`.

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

##  <a name="releasebuffersetlength"></a>  CSimpleStringT::ReleaseBufferSetLength

Gibt die Steuerung des vom reservierten Puffers frei [GetBuffer](#getbuffer).

### <a name="syntax"></a>Syntax

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parameter

*nNewLength*<br/>
Die Länge der Zeichenfolge, die freigegeben wird

### <a name="remarks"></a>Hinweise

Diese Funktion ist funktional mit [ReleaseBuffer](#releasebuffer) mit dem Unterschied, dass eine gültige Länge für das String-Objekt übergeben werden muss.

##  <a name="setat"></a>  CSimpleStringT::SetAt

Legt ein einzelnes Zeichen aus einer `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parameter

*iChar*<br/>
Nullbasierte Index des Zeichens in der `CSimpleStringT` Objekt. Die *iChar* Parameter muss größer als oder gleich 0 und kleiner als der Rückgabewert von [GetLength](#getlength).

*ch*<br/>
Das neue Zeichen.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Überschreiben des Zeichens an *iChar*. Diese Methode wird die Zeichenfolge nicht vergrößern, wenn *iChar* überschreitet die Begrenzungen des die vorhandene Zeichenfolge.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>  CSimpleStringT::SetManager

Gibt an, der Speicher-Manager, der die `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parameter

*pStringMgr*<br/>
Ein Zeiger auf den neuen Speichermanager.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Angeben eines neuen Speichers-Manager verwendet werden, indem die `CSimpleStringT` Objekt. Weitere Informationen zu Speicher-Manager und String-Objekten, finden Sie unter [Speicherverwaltung und CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>  CSimpleStringT::SetString

Legt die Zeichenfolge von einem `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parameter

*pszSrc*<br/>
Ein Zeiger auf eine Null-terminierte Zeichenfolge.

*nLength*<br/>
Die Anzahl der Zeichen im *PszSrc*.

### <a name="remarks"></a>Hinweise

Kopieren eine Zeichenfolge in die `CSimpleStringT` Objekt. `SetString` überschreibt die ältere Zeichenfolgendaten in den Puffer.

Beide Versionen der `SetString` überprüfen, ob *PszSrc* ein null-Zeiger ist, und wenn es sich handelt, löst einen E_INVALIDARG-Fehler.

Die Version für einen Parameter des `SetString` erwartet *PszSrc* auf eine Null-terminierte Zeichenfolge verweisen.

Die beiden Parameter-Version des `SetString` außerdem erwartet, dass *PszSrc* eine Null-terminierte Zeichenfolge. Er verwendet *nLength* als die Länge der Zeichenfolge, wenn sie zuerst einen null-Terminator auftritt.

Die beiden Parameter-Version des `SetString` überprüft auch, ob *PszSrc* verweist auf eine Position des aktuellen Puffers in `CSimpleStringT`. In diesem speziellen Fall `SetString` verwendet eine Arbeitsspeicher-Copy-Funktion, die die Daten der Zeichenfolge nicht überschrieben wird, wie sie die Zeichenfolgendaten zurück in den Puffer kopiert.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>  CSimpleStringT::StringLength

Gibt die Anzahl der Zeichen in der angegebenen Zeichenfolge zurück.

### <a name="syntax"></a>Syntax

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parameter

*psz*<br/>
Ein Zeiger auf eine Null-terminierte Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen in *Psz*; ein null-Terminator wird dabei nicht mitgezählt.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zum Abrufen der Anzahl von Zeichen in der Zeichenfolge verweist *Psz*.

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>  CSimpleStringT::Truncate

Schneidet die Zeichenfolge, die die neue Länge ab.

### <a name="syntax"></a>Syntax

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parameter

*nNewLength*<br/>
Die neue Länge der Zeichenfolge.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um den Inhalt der Zeichenfolge, die die neue Länge abgeschnitten.

> [!NOTE]
>  Dies wirkt sich nicht auf die zugeordnete Länge des Puffers. Zum Vergrößern, oder verringern die aktuellen Puffer, finden Sie unter [FreeExtra](#freeextra) und [Preallocate](#preallocate).

### <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von `CSimpleStringT::Truncate`.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

##  <a name="unlockbuffer"></a>  CSimpleStringT::UnlockBuffer

Entsperrt den Puffer mit der `CSimpleStringT` Objekt.

### <a name="syntax"></a>Syntax

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um den Verweiszähler der Zeichenfolge auf 1 zurückgesetzt.

Die `CSimpleStringT` ruft der Destruktor automatisch `UnlockBuffer` um sicherzustellen, dass der Puffer nicht gesperrt ist, wenn der Destruktor aufgerufen wird. Ein Beispiel dieser Methode finden Sie unter [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>  CSimpleStringT:: ~ CSimpleStringT

Zerstört ein `CSimpleStringT`-Objekt.

### <a name="syntax"></a>Syntax

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode zerstört die `CSimpleStringT` Objekt.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Freigegebene ATL-/MFC-Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md)
