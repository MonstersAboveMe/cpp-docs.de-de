---
title: _putenv_s, _wputenv_s
ms.date: 11/04/2016
apiname:
- _wputenv_s
- _putenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: f675c2c0a2b12db3cce841dd0db9fa722393f1b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357862"
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s

Erstellt, ändert oder entfernt Umgebungsvariablen. Dies sind Versionen von [_putenv, _wputenv](putenv-wputenv.md), enthalten aber Sicherheitserweiterungen wie unter [Sicherheitserweiterungen im CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>Parameter

*varname*<br/>
Der Umgebungsvariablenname.

*value_string*<br/>
Der Wert, auf den die Umgebungsvariable festgelegt wird.

## <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück, wenn erfolgreich, oder einen Fehlercode.

### <a name="error-conditions"></a>Fehlerbedingungen

|*varname*|*value_string*|Rückgabewert|
|------------|-------------|------------------|
|**NULL**|any|**EINVAL**|
|any|**NULL**|**EINVAL**|

Wenn einer dieser Fehlerzustände auftritt, wird ein Handler für ungültige Parameter von diesen Funktionen aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, um den Vorgang fortzusetzen, geben diese Funktionen zurück **EINVAL** und **Errno** zu **EINVAL**.

## <a name="remarks"></a>Hinweise

Die **_putenv_s** Funktion fügt neue Umgebungsvariablen hinzu oder ändert die Werte vorhandener Umgebungsvariablen. Umgebungsvariablen definieren die Umgebung, in der ein Prozess ausgeführt wird (beispielsweise der Standardsuchpfad für die mit einem Programm zu verknüpfenden Bibliotheken). **_wputenv_s** ist eine Breitzeichen-Version von **_putenv_s**; die *Envstring* Argument **_wputenv_s** ist eine Breitzeichen-Zeichenfolge.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*VarName* ist der Name der Umgebungsvariablen hinzugefügt oder geändert werden und *Value_string* ist der Wert der Variablen. Wenn *Varname* ist bereits Teil der Umgebung durch seinen Wert ersetzt *Value_string*ist, andernfalls das neue *Varname* Variable und die zugehörige *Value_string*  der Umgebung hinzugefügt werden. Sie können eine Variable aus der Umgebung entfernen, indem Sie eine leere Zeichenfolge angeben (d. h. "") für *Value_string*.

**_putenv_s** und **_wputenv_s** beeinflussen nur die Umgebung, die für den aktuellen Prozess lokal ist; Sie können nicht zum Ändern der Befehlsebene-Umgebung. Diese Funktionen funktionieren nur bei Datenstrukturen, auf die die Laufzeitbibliothek zugreifen kann, aber nicht bei dem Umgebungssegment, das vom Betriebssystem für einen Prozess erstellt wurde. Wenn der aktuelle Prozess beendet wird, wird die Umgebung auf die Ebene des aufrufenden Prozesses zurückgesetzt (in den meisten Fällen die Betriebssystemebene). Die geänderte Umgebung kann jedoch an alle neue Prozesse, die vom erstellten übergeben werden **_spawn**, **_exec**, oder **System**, und diese neuen Prozesse rufen alle neuen Elemente, die hinzugefügt von **_putenv_s** und **_wputenv_s**.

Einen Umgebungseintrag nicht direkt geändert werden. Verwenden Sie stattdessen **_putenv_s** oder **_wputenv_s** , ihn zu ändern. Direkte Loslösen von Elementen von der **_environ []** globales Array kann dazu führen, dass ungültigen Speicher adressiert werden.

**Getenv** und **_putenv_s** verwenden die globale Variable **_environ** auf die umgebungstabelle zuzugreifen; **_wgetenv** und **_wputenv_s** verwenden **_wenviron**. **_putenv_s** und **_wputenv_s** ändern möglicherweise den Wert der **_environ** und **_wenviron**, und dadurch ungültig. die *Envp*Argument **main** und **_wenvp** Argument **Wmain**. Es ist daher sicherer mit **_environ** oder **_wenviron** auf die Umgebungsinformationen zuzugreifen. Weitere Informationen über die Beziehung von **_putenv_s** und **_wputenv_s** mit globalen Variablen finden Sie unter [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Die **_putenv_s** und **_getenv_s** Funktionsreihe sind nicht threadsicher. **_getenv_s** gibt möglicherweise einen Zeichenfolgenzeiger beim zurück **_putenv_s** verändern der Zeichenfolge ist, und gelegentlich Fehler bewirken. Stellen Sie sicher, dass Aufrufe dieser Funktionen synchronisiert sind.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel, das zeigt, wie Sie mit **_putenv_s**, finden Sie unter [Getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Siehe auch

[Prozess- und Umgebungssteuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
