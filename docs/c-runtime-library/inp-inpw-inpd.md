---
title: _inp, _inpw, _inpd
ms.date: 11/04/2016
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: 0915b7a98b10137b37025eb59161bc98c27ae7b3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748345"
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd

Eingaben von einem Port, einem Byte (`_inp`), einem Wort (`_inpw`) oder von einem Doppelwort (`_inpd`).

> [!IMPORTANT]
>  Diese Funktionen sind veraltet. Von Visual Studio 2015 an sind sie nicht in der CRT verfügbar.

> [!IMPORTANT]
>  Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

#### <a name="parameters"></a>Parameter

*Port*<br/>
E/A-Portnummer.

## <a name="return-value"></a>Rückgabewert

Die Funktionen geben das aus `port`gelesene Byte, Wort oder Doppelwort zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Anmerkungen

Die Funktionen `_inp`, `_inpw`und `_inpd` lesen aus dem angegebenen Eingangsport jeweils ein Byte, ein Wort und ein Doppelwort. Der Eingabewert kann jede beliebige kurze ganze Zahl ohne Vorzeichen im Bereich von 0 bis 65.535 sein.

Da diese Funktionen direkt aus einem E/A-Port lesen, können sie nicht im Benutzercode verwendet werden.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|`_inp`|\<conio.h>|
|`_inpw`|\<conio.h>|
|`_inpd`|\<conio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Siehe auch

[Konsole und Port-E/A](../c-runtime-library/console-and-port-i-o.md)<br/>
[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
