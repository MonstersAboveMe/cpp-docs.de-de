---
title: raise
ms.date: 1/02/2018
apiname:
- raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 68d1cc653b955e607648e4d30562d2b77e3520e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358052"
---
# <a name="raise"></a>raise

Sendet ein Signal an das ausführende Programm.

> [!NOTE]
> Verwenden Sie diese Methode nicht, eine Microsoft Store-app, mit Ausnahme von Herunterfahren in Test- oder Debugszenarien. Programmgesteuerte oder UI-Methoden zum Schließen einer Store-app sind nicht zulässig, gemäß der [Microsoft Store Richtlinien](/legal/windows/agreements/store-policies). Weitere Informationen finden Sie unter [UWP-app-Lebenszyklus](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Syntax

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parameter

*sig*<br/>
Auszulösendes Signal.

## <a name="return-value"></a>Rückgabewert

Bei Erfolg gibt **raise** 0 zurück . Andernfalls gibt es einen Wert ungleich 0 (null) zurück.

## <a name="remarks"></a>Hinweise

Die **raise**-Funktion sendet *sig* an das ausführende Programm. Wenn ein vorheriger Aufruf von **signal** eine Signalverarbeitungsfunktion für *sig* installiert hat, führt **raise** diese Funktion aus. Wenn keine Handlerfunktion installiert wurde, wird die dem Signalwert *sig* zugeordnete Standardaktion wie folgt ausgeführt.

|Signal|Bedeutung|Standard|
|------------|-------------|-------------|
|**SIGABRT**|Nicht ordnungsgemäße Beendigung|Beendet das aufrufende Programm mit Exitcode 3|
|**SIGFPE**|Gleitkommafehler|Beendet das aufrufende Programm|
|**SIGILL**|Ungültige Anweisung|Beendet das aufrufende Programm|
|**SIGINT**|STRG+C-Unterbrechung|Beendet das aufrufende Programm|
|**SIGSEGV**|Ungültiger Speicherzugriff|Beendet das aufrufende Programm|
|**SIGTERM**|An das Programm gesendete Beendigungsanforderung|Ignoriert das Signal|

Wenn das Argument kein gültiges Signal gemäß den oberen Angaben ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Die Funktion legt fest, wenn nicht behandelt, **Errno** zu **EINVAL** und gibt einen Wert ungleich NULL zurück.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**raise**|\<signal.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Prozess- und Umgebungssteuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
