---
title: _strdec, _wcsdec, _mbsdec, _mbsdec_l
ms.date: 11/04/2016
apiname:
- _wcsdec
- _strdec
- _mbsdec
- _mbsdec_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strdec
- mbsdec_l
- strdec
- _mbsdec
- _mbsdec_l
- mbsdec
- wcsdec
- _wcsdec
helpviewer_keywords:
- mbsdec_l function
- mbsdec function
- tcsdec function
- _tcsdec function
- _strdec function
- _wcsdec function
- _mbsdec_l function
- strdec function
- wcsdec function
- _mbsdec function
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
ms.openlocfilehash: 7e88bcf5bf7ffc5eba6feecd545cda8f7950829c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353880"
---
# <a name="strdec-wcsdec-mbsdec-mbsdecl"></a>_strdec, _wcsdec, _mbsdec, _mbsdec_l

Setzt einen Zeichenfolgenzeiger um ein Zeichen zurück.

> [!IMPORTANT]
> **Mbsdec** und **Mbsdec_l** kann nicht verwendet werden, in Anwendungen, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
unsigned char *_strdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned wchar_t *_wcsdec(
   const unsigned wchar_t *start,
   const unsigned wchar_t *current
);
unsigned char *_mbsdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned char *_mbsdec_l(
   const unsigned char *start,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*start*<br/>
Zeiger auf ein beliebiges Zeichen (oder für **_mbsdec** und **_mbsdec_l**, das erste Byte eines multibytezeichens) in der Quellzeichenfolge *starten* muss vorangehen *aktuelle* in der Quellzeichenfolge.

*current*<br/>
Zeiger auf ein beliebiges Zeichen (oder für **_mbsdec** und **_mbsdec_l**, das erste Byte eines multibytezeichens) in der Quellzeichenfolge *aktuelle* müssen *starten* in der Quellzeichenfolge.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_mbsdec**, **_mbsdec_l**, **_strdec**, und **_wcsdec** jeweils einen Zeiger zurück, auf das Zeichen, die unmittelbar vorangestellt *aktuelle*; **_mbsdec** gibt **NULL** Wenn der Wert des *starten* ist größer als oder gleich dem des *aktuelle*. **_tcsdec** Zuordnungen, die diese Funktionen und der Rückgabewert hängt von der Zuordnung.

## <a name="remarks"></a>Hinweise

Die **_mbsdec** und **_mbsdec_l** Funktionen geben einen Zeiger auf das erste Byte des multibytezeichens, die unmittelbar vorangestellt *aktuelle* in die Zeichenfolge, enthält *starten*.

Der Ausgabewert wird von der Einstellung beeinflusst die **LC_CTYPE** -kategorieeinstellung des Gebietsschemas, siehe [Setlocale, _wsetlocale](setlocale-wsetlocale.md) für Weitere Informationen.  **_mbsdec** erkennt multibytezeichensequenzen gemäß dem Gebietsschema, das derzeit verwendet wird, wird beim **_mbsdec_l** ist identisch, verwendet jedoch stattdessen den Gebietsschemaparameter, der übergeben wird. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Wenn *starten* oder *aktuelle* ist **NULL**, Handler für ungültige Parameter aufgerufen, siehe [Parametervalidierung](../../c-runtime-library/parameter-validation.md). Diese Funktion gibt zurück, wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, **EINVAL** und **Errno** zu **EINVAL**.

> [!IMPORTANT]
> Diese Funktionen sind möglicherweise für Pufferüberlaufrisiken anfällig. Pufferüberläufe können für Systemangriffe eingesetzt werden, da sie zu einer unbefugten Ausweitung der Berechtigungen führen. Weitere Informationen finden Sie unter [Vermeiden von Pufferüberläufen](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsdec**|**_strdec**|**_mbsdec**|**_wcsdec**|

**_strdec** und **_wcsdec** sind Single-Byte-Zeichen und Breitzeichen von **_mbsdec** und **_mbsdec_l**. **_strdec** und **_wcsdec** werden nur für diese Zuordnung bereitgestellt und sollte nicht anderweitig verwendet werden.

Weitere Informationen finden Sie unter [Verwenden von Zuordnungen für generischen Text](../../c-runtime-library/using-generic-text-mappings.md) und [Textzuordnungen für generischen Text](../../c-runtime-library/generic-text-mappings.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_mbsdec**|\<mbstring.h>|\<mbctype.h>|
|**_mbsdec_l**|\<mbstring.h>|\<mbctype.h>|
|**_strdec**|\<tchar.h>||
|**_wcsdec**|\<tchar.h>||

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von **_tcsdec**.

```cpp
// crt_tcsdec.cpp
// Compile by using: cl /EHsc crt_tcsdec.cpp
#include <iostream>
#include <tchar.h>
using namespace std;

int main()
{
   const TCHAR *str = _T("12345");
   cout << "str: " << str << endl;

   const TCHAR *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   TCHAR *answer;
   answer = _tcsdec( str, str2 );
   cout << "answer: " << answer << endl;

   return (0);
}
```

Das folgende Beispiel veranschaulicht die Verwendung von **_mbsdec**.

```cpp
// crt_mbsdec.cpp
// Compile by using: cl /EHsc crt_mbsdec.c
#include <iostream>
#include <mbstring.h>
using namespace std;

int main()
{
   char *str = "12345";
   cout << "str: " << str << endl;

   char *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   unsigned char *answer;
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));

   cout << "answer: " << answer << endl;

   return (0);
}
```

## <a name="see-also"></a>Siehe auch

[Zeichenfolgenbearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
