---
title: time, _time32, _time64
ms.date: 11/06/2018
apiname:
- time
- _time64
- _time32
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- time
- _time64
- time/time
- time/_time32
- time/_time64
- _time32
helpviewer_keywords:
- time32 function
- _time32 function
- _time64 function
- time functions
- system time
- time64 function
ms.assetid: 280e00f2-2b93-4ece-94cd-e048484c6cc7
ms.openlocfilehash: 693b70b3682876d7e6c3721f5d06aa13d31abb96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155588"
---
# <a name="time-time32-time64"></a>time, _time32, _time64

Ruft die Systemzeit ab.

## <a name="syntax"></a>Syntax

```C
time_t time( time_t *destTime );
__time32_t _time32( __time32_t *destTime );
__time64_t _time64( __time64_t *destTime );
```

### <a name="parameters"></a>Parameter

*destTime*<br/>
Zeiger auf den Speicherort für die Zeit.

## <a name="return-value"></a>Rückgabewert

Gibt die Zeit, als Sekunden seit Mitternacht des 1. Januar 1970, oder-1 im Fall eines Fehlers verstrichen sind.

## <a name="remarks"></a>Hinweise

Die **Zeit** Funktion gibt die Anzahl der Sekunden seit Mitternacht vergangenen (00: 00:00), 1. Januar 1970, koordinierte Weltzeit (UTC), entsprechend der Systemuhr. Der zurückgegebene Wert befindet sich in den Speicherort von *DestTime*. Dieser Parameter ist möglicherweise **NULL**, wobei der Rückgabewert nicht gespeichert ist.

**Zeit** ist ein Wrapper für **_time64** und **Time_t** ist, in der Standardeinstellung entspricht **__time64_t**. Wenn Sie erzwingen, dass den Compiler interpretiert müssen **Time_t** als das alte 32-Bit **Time_t**, können Sie definieren **_USE_32BIT_TIME_T**. Dies ist nicht zu empfehlen, weil die Anwendung nach dem 18. Januar 2038 fehlschlagen kann. Die Verwendung dieses Makros ist auf 64-Bit-Plattformen nicht zulässig.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher C-Header|Erforderlicher C++-Header|
|-------|------|---------------------|
|**time**, **\_time32**, **\_time64**|\<time.h>|\<CTime > oder \<time.h >|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_times.c
// compile with: /W3
// This program demonstrates these time and date functions:
//      time         _ftime    ctime_s     asctime_s
//      _localtime64_s    _gmtime64_s    mktime    _tzset
//      _strtime_s     _strdate_s  strftime
//
// Also the global variable:
//      _tzname
//
// Turn off deprecated unsafe CRT function warnings
#define _CRT_SECURE_NO_WARNINGS 1

#include <time.h>
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/timeb.h>
#include <string.h>

int main()
{
    char tmpbuf[128], timebuf[26], ampm[] = "AM";
    time_t ltime;
    struct _timeb tstruct;
    struct tm today, gmt, xmas = { 0, 0, 12, 25, 11, 93 };
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    _strtime_s( tmpbuf, 128 );
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    _strdate_s( tmpbuf, 128 );
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

    // Get UNIX-style time and display as number and string.
    time( &ltime );
    printf( "Time in seconds since UTC 1/1/70:\t%lld\n", (long long)ltime );
    err = ctime_s(timebuf, 26, &ltime);
    if (err)
    {
        printf("ctime_s failed due to an invalid argument.");
        exit(1);
    }
    printf( "UNIX time and date:\t\t\t%s", timebuf );

    // Display UTC.
    err = _gmtime64_s( &gmt, &ltime );
    if (err)
    {
        printf("_gmtime64_s failed due to an invalid argument.");
    }
    err = asctime_s(timebuf, 26, &gmt);
    if (err)
    {
        printf("asctime_s failed due to an invalid argument.");
        exit(1);
    }
    printf( "Coordinated universal time:\t\t%s", timebuf );

    // Convert to time structure and adjust for PM if necessary.
    err = _localtime64_s( &today, &ltime );
    if (err)
    {
        printf("_localtime64_s failed due to an invalid argument.");
        exit(1);
    }
    if ( today.tm_hour >= 12 )
    {
        strcpy_s( ampm, sizeof(ampm), "PM" );
        today.tm_hour -= 12;
    }
    if ( today.tm_hour == 0 )  // Adjust if midnight hour.
        today.tm_hour = 12;

    // Convert today into an ASCII string
    err = asctime_s(timebuf, 26, &today);
    if (err)
    {
        printf("asctime_s failed due to an invalid argument.");
        exit(1);
    }

    // Note how pointer addition is used to skip the first 11
    // characters and printf is used to trim off terminating
    // characters.
    //
    printf( "12-hour time:\t\t\t\t%.8s %s\n",
        timebuf + 11, ampm );

    // Print additional time information.
    _ftime( &tstruct ); // C4996
    // Note: _ftime is deprecated; consider using _ftime_s instead
    printf( "Plus milliseconds:\t\t\t%u\n", tstruct.millitm );
    printf( "Zone difference in hours from UTC:\t%u\n",
             tstruct.timezone/60 );
    printf( "Time zone name:\t\t\t\t%s\n", _tzname[0] ); //C4996
    // Note: _tzname is deprecated; consider using _get_tzname
    printf( "Daylight savings:\t\t\t%s\n",
             tstruct.dstflag ? "YES" : "NO" );

    // Make time for noon on Christmas, 1993.
    if( mktime( &xmas ) != (time_t)-1 )
    {
        err = asctime_s(timebuf, 26, &xmas);
        if (err)
        {
            printf("asctime_s failed due to an invalid argument.");
            exit(1);
        }
        printf( "Christmas\t\t\t\t%s\n", timebuf );
    }

    // Use time structure to build a customized time string.
    err = _localtime64_s( &today, &ltime );
    if (err)
    {
        printf(" _localtime64_s failed due to invalid arguments.");
        exit(1);
    }

    // Use strftime to build a customized time string.
    strftime( tmpbuf, 128,
              "Today is %A, day %d of %B in the year %Y.\n", &today );
    printf( tmpbuf );
}
```

```Output
OS time:            13:51:23
OS date:            04/25/03
Time in seconds since UTC 1/1/70:   1051303883
UNIX time and date:         Fri Apr 25 13:51:23 2003
Coordinated universal time:      Fri Apr 25 20:51:23 2003
12-hour time:            01:51:23 PM
Plus milliseconds:         552
Zone difference in hours from UTC:   8
Time zone name:            Pacific Standard Time
Daylight savings:         YES
Christmas            Sat Dec 25 12:00:00 1993

Today is Friday, day 25 of April in the year 2003.
```

## <a name="see-also"></a>Siehe auch

[Uhrzeitverwaltung](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[asctime_s, _wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime, _ftime32, _ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[_utime, _utime32, _utime64, _wutime, _wutime32, _wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
