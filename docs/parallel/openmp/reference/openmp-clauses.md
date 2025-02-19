---
title: OpenMP-Klauseln
ms.date: 03/20/2019
f1_keywords:
- OpenMP clauses
- copyin
- copyprivate
- default
- firstprivate
- if
- lastprivate
- nowait
- num_threads
- ordered
- private
- reduction
- schedule
- shared
helpviewer_keywords:
- OpenMP clauses
- copyin OpenMP clause
- copyprivate OpenMP clause
- default OpenMP clause
- defaults, OpenMP clause
- firstprivate OpenMP clause
- if OpenMP clause
- lastprivate OpenMP clause
- nowait OpenMP clause
- num_threads OpenMP clause
- ordered OpenMP clause
- private OpenMP clause
- reduction OpenMP clause
- schedule OpenMP clause
- shared OpenMP clause
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
ms.openlocfilehash: 590cb7d619895a04dfc511b6b77dad4074dc3f42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362659"
---
# <a name="openmp-clauses"></a>OpenMP-Klauseln

Enthält Links zu den Klauseln, die in der OpenMP-API verwendet.

Visual C++ unterstützt die folgenden OpenMP-Klauseln.

Für allgemeine Attribute:

|Klausel|Beschreibung|
|------|-----------|
|[if](#if-openmp)|Gibt an, ob eine Schleife parallel oder seriell ausgeführt werden soll.|
|[num_threads](#num-threads)|Legt die Anzahl der Threads in einem Team Thread fest.|
|[ordered](#ordered-openmp-clauses)|Erforderlich für eine parallele [für](openmp-directives.md#for-openmp) Anweisung Wenn ein [sortiert](openmp-directives.md#ordered-openmp-directives) -Direktive ist, in der Schleife verwendet werden.|
|[schedule](#schedule)|Gilt für die [für](openmp-directives.md#for-openmp) Richtlinie.|
|[nowait](#nowait)|Überschreibt die Grenze, die in einer Anweisung implizit.|

Für die Datenfreigabe Attribute:

|Klausel|Beschreibung|
|------|-----------|
|[private](#private-openmp)|Gibt an, dass jeder Thread eine eigene Instanz einer Variablen zugewiesen werden soll.|
|[firstprivate](#firstprivate)|Gibt an, dass jeder Thread eine eigene Instanz einer Variablen zugewiesen werden soll, und die Variable mit dem Wert der Variablen initialisiert werden soll, da sie vor dem das parallele Konstrukt vorhanden ist.|
|[lastprivate](#lastprivate)|Gibt an, dass der umschließenden Kontext Version der Variablen ist gleich der privaten Version der Thread der letzten Iteration (for-Schleife-Konstrukt) oder der letzte Abschnitt (#pragma Abschnitte) ausgeführt wird.|
|[shared](#shared-openmp)|Gibt an, dass eine oder mehrere Variablen, die auf allen Threads freigegeben werden soll.|
|[default](#default-openmp)|Gibt das Verhalten ohne bereichseinschränkung Variablen in einem parallelen Bereich an.|
|[reduction](#reduction)|Gibt an, dass eine oder mehrere Variablen, die für jeden Thread privat sind ein Reduzierungsvorgang am Ende des parallelen Bereichs werden.|
|[copyin](#copyin)|Ermöglicht die Threads der master-Thread-Wert, für den Zugriff auf eine [Threadprivate](openmp-directives.md#threadprivate) Variable.|
|[copyprivate](#copyprivate)|Gibt an, dass eine oder mehrere Variablen, die auf allen Threads freigegeben werden soll.|

## <a name="copyin"></a>copyin

Ermöglicht die Threads der master-Thread-Wert, für den Zugriff auf eine [Threadprivate](openmp-directives.md#threadprivate) Variable.

```
copyin(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Die `threadprivate` Variable, die mit den Wert der Variablen in der master-Thread initialisiert wird, wie sie vor dem das parallele Konstrukt vorhanden ist.

### <a name="remarks"></a>Hinweise

`copyin` gilt für die folgenden Anweisungen:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)

Weitere Informationen finden Sie unter [2.7.2.7 Copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

### <a name="example"></a>Beispiel

Finden Sie unter [Threadprivate](openmp-directives.md#threadprivate) ein Beispiel der Verwendung von `copyin`.

## <a name="copyprivate"></a>copyprivate

Gibt an, dass eine oder mehrere Variablen, die auf allen Threads freigegeben werden soll.

```
copyprivate(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Eine oder mehrere Variablen freigeben. Wenn mehr als eine Variable angegeben ist, trennen Sie Namen durch ein Komma.

### <a name="remarks"></a>Hinweise

`copyprivate` gilt für die [einzelne](openmp-directives.md#single) Richtlinie.

Weitere Informationen finden Sie unter [2.7.2.8 Copyprivate](../../../parallel/openmp/2-7-2-8-copyprivate.md).

### <a name="example"></a>Beispiel

```cpp
// omp_copyprivate.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

float x, y, fGlobal = 1.0;
#pragma omp threadprivate(x, y)

float get_float() {
   fGlobal += 0.001;
   return fGlobal;
}

void use_float(float f, int t) {
   printf_s("Value = %f, thread = %d\n", f, t);
}

void CopyPrivate(float a, float b) {
   #pragma omp single copyprivate(a, b, x, y)
   {
      a = get_float();
      b = get_float();
      x = get_float();
      y = get_float();
    }

   use_float(a, omp_get_thread_num());
   use_float(b, omp_get_thread_num());
   use_float(x, omp_get_thread_num());
   use_float(y, omp_get_thread_num());
}

int main() {
   float a = 9.99, b = 123.456;

   printf_s("call CopyPrivate from a single thread\n");
   CopyPrivate(9.99, 123.456);

   printf_s("call CopyPrivate from a parallel region\n");
   #pragma omp parallel
   {
      CopyPrivate(a, b);
   }
}
```

```Output
call CopyPrivate from a single thread
Value = 1.001000, thread = 0
Value = 1.002000, thread = 0
Value = 1.003000, thread = 0
Value = 1.004000, thread = 0
call CopyPrivate from a parallel region
Value = 1.005000, thread = 0
Value = 1.005000, thread = 1
Value = 1.006000, thread = 0
Value = 1.006000, thread = 1
Value = 1.007000, thread = 0
Value = 1.007000, thread = 1
Value = 1.008000, thread = 0
Value = 1.008000, thread = 1
```

## <a name="default-openmp"></a>default

Gibt das Verhalten ohne bereichseinschränkung Variablen in einem parallelen Bereich an.

```
default(shared | none)
```

### <a name="remarks"></a>Hinweise

`shared`, die gilt Wenn die `default` -Klausel nicht angegeben ist, bedeutet, dass jede Variable in einem parallelen Bereich behandelt wird, als ob es angegeben wurden, mit der [freigegebenen](#shared-openmp) Klausel. `none` bedeutet, dass alle Variablen, die in einem parallelen Bereich, der im Bereich mit einer nicht sind, verwendet der [private](#private-openmp), [freigegebenen](#shared-openmp), [Verringerung](#reduction), [Firstprivate](#firstprivate), oder [Lastprivate](#lastprivate) -Klausel bewirkt, dass ein Compilerfehler ausgegeben.

`default` gilt für die folgenden Anweisungen:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)

Weitere Informationen finden Sie unter [2.7.2.5 Standard](../../../parallel/openmp/2-7-2-5-default.md).

### <a name="example"></a>Beispiel

Finden Sie unter [private](#private-openmp) ein Beispiel der Verwendung von `default`.

## <a name="firstprivate"></a>firstprivate

Gibt an, dass jeder Thread eine eigene Instanz einer Variablen zugewiesen werden soll, und die Variable mit dem Wert der Variablen initialisiert werden soll, da sie vor dem das parallele Konstrukt vorhanden ist.

```
firstprivate(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Die Instanzen in jeder Thread und die Variable wird mit den Wert der Variablen, initialisiert werden, da sie vor dem das parallele Konstrukt vorhanden ist. Wenn mehr als eine Variable angegeben ist, trennen Sie Namen durch ein Komma.

### <a name="remarks"></a>Hinweise

`firstprivate` gilt für die folgenden Anweisungen:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Abschnitte](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Weitere Informationen finden Sie unter [2.7.2.2 Firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

### <a name="example"></a>Beispiel

Ein Beispiel der Verwendung von `firstprivate`, siehe das Beispiel in [private](#private-openmp).

## <a name="if-openmp"></a>if (OpenMP)

Gibt an, ob eine Schleife parallel oder seriell ausgeführt werden soll.

```
if(expression)
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Ein ganzzahliger Ausdruck, der, wenn er (ungleich null), "true" ausgewertet wird der Code in den parallelen Bereich zur parallelen Ausführung verursacht. Wenn der Ausdruck "false" (null) ergibt, wird der parallele Bereich seriell (von einem einzelnen Thread) ausgeführt.

### <a name="remarks"></a>Hinweise

`if` gilt für die folgenden Anweisungen:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)

Weitere Informationen finden Sie unter [2.3 parallel-Konstrukt](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_if.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void test(int val)
{
    #pragma omp parallel if (val)
    if (omp_in_parallel())
    {
        #pragma omp single
        printf_s("val = %d, parallelized with %d threads\n",
                 val, omp_get_num_threads());
    }
    else
    {
        printf_s("val = %d, serialized\n", val);
    }
}

int main( )
{
    omp_set_num_threads(2);
    test(0);
    test(2);
}
```

```Output
val = 0, serialized
val = 2, parallelized with 2 threads
```

## <a name="lastprivate"></a>lastprivate

Gibt an, dass der umschließenden Kontext Version der Variablen ist gleich der privaten Version der Thread der letzten Iteration (for-Schleife-Konstrukt) oder der letzte Abschnitt (#pragma Abschnitte) ausgeführt wird.

```
lastprivate(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Die Variable, die gleich der privaten Version der Thread ausgeführt, der letzten Iteration (for-Schleife-Konstrukt) oder der letzte Abschnitt (#pragma Abschnitte wird) festgelegt ist.

### <a name="remarks"></a>Hinweise

`lastprivate` gilt für die folgenden Anweisungen:

- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)

Weitere Informationen finden Sie unter [2.7.2.3 Lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).

### <a name="example"></a>Beispiel

Finden Sie unter [Zeitplan](#schedule) ein Beispiel der Verwendung von `lastprivate` Klausel.

## <a name="nowait"></a>nowait

Überschreibt die Grenze, die in einer Anweisung implizit.

```
nowait
```

### <a name="remarks"></a>Hinweise

`nowait` gilt für die folgenden Anweisungen:

- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Weitere Informationen finden Sie unter [2.4.1 for-Konstrukt](../../../parallel/openmp/2-4-1-for-construct.md), [2.4.2 sections-Konstrukt](../../../parallel/openmp/2-4-2-sections-construct.md), und [2.4.3 einzelne erstellen](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_nowait.cpp
// compile with: /openmp /c
#include <stdio.h>

#define SIZE 5

void test(int *a, int *b, int *c, int size)
{
    int i;
    #pragma omp parallel
    {
        #pragma omp for nowait
        for (i = 0; i < size; i++)
            b[i] = a[i] * a[i];

        #pragma omp for nowait
        for (i = 0; i < size; i++)
            c[i] = a[i]/2;
    }
}

int main( )
{
    int a[SIZE], b[SIZE], c[SIZE];
    int i;

    for (i=0; i<SIZE; i++)
        a[i] = i;

    test(a,b,c, SIZE);

    for (i=0; i<SIZE; i++)
        printf_s("%d, %d, %d\n", a[i], b[i], c[i]);
}
```

```Output
0, 0, 0
1, 1, 0
2, 4, 1
3, 9, 1
4, 16, 2
```

## <a name="num-threads"></a>num_threads

Legt die Anzahl der Threads in einem Team Thread fest.

```
num_threads(num)
```

### <a name="parameters"></a>Parameter

*num*<br/>
Die Anzahl von threads

### <a name="remarks"></a>Hinweise

Die `num_threads` -Klausel besitzt die gleiche Funktionalität wie die [Omp_set_num_threads](openmp-functions.md#omp-set-num-threads) Funktion.

`num_threads` gilt für die folgenden Anweisungen:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)

Weitere Informationen finden Sie unter [2.3 parallel-Konstrukt](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Beispiel

Finden Sie unter [parallele](openmp-directives.md#parallel) ein Beispiel der Verwendung von `num_threads` Klausel.

## <a name="ordered-openmp-clauses"></a>Sortiert

Erforderlich für eine parallele [für](openmp-directives.md#for-openmp) Anweisung Wenn ein [sortiert](openmp-directives.md#ordered-openmp-directives) -Direktive ist, in der Schleife verwendet werden.

```
ordered
```

### <a name="remarks"></a>Hinweise

`ordered` gilt für die [für](openmp-directives.md#for-openmp) Richtlinie.

Weitere Informationen finden Sie unter [2.4.1 for-Konstrukt](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Beispiel

Finden Sie unter [sortiert](openmp-directives.md#ordered-openmp-directives) ein Beispiel der Verwendung von `ordered` Klausel.

## <a name="private-openmp"></a>Private

Gibt an, dass jeder Thread eine eigene Instanz einer Variablen zugewiesen werden soll.

```
private(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Die Variable, die Instanzen in jedem Thread verwenden.

### <a name="remarks"></a>Hinweise

`private` gilt für die folgenden Anweisungen:

- [for](openmp-directives.md#for-openmp)
- [parallel](openmp-directives.md#parallel)
- [Abschnitte](openmp-directives.md#sections-openmp)
- [single](openmp-directives.md#single)

Weitere Informationen finden Sie unter [2.7.2.1 private](../../../parallel/openmp/2-7-2-1-private.md).

### <a name="example"></a>Beispiel

```c
// openmp_private.c
// compile with: /openmp
#include <windows.h>
#include <assert.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SLEEP_THREAD 1
#define NUM_LOOPS 2

enum Types {
   ThreadPrivate,
   Private,
   FirstPrivate,
   LastPrivate,
   Shared,
   MAX_TYPES
};

int nSave[NUM_THREADS][MAX_TYPES][NUM_LOOPS] = {{0}};
int nThreadPrivate;

#pragma omp threadprivate(nThreadPrivate)
#pragma warning(disable:4700)

int main() {
   int nPrivate = NUM_THREADS;
   int nFirstPrivate = NUM_THREADS;
   int nLastPrivate = NUM_THREADS;
   int nShared = NUM_THREADS;
   int nRet = 0;
   int i;
   int j;
   int nLoop = 0;

   nThreadPrivate = NUM_THREADS;
   printf_s("These are the variables before entry "
           "into the parallel region.\n");
   printf_s("nThreadPrivate = %d\n", nThreadPrivate);
   printf_s("      nPrivate = %d\n", nPrivate);
   printf_s(" nFirstPrivate = %d\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d\n", nLastPrivate);
   printf_s("       nShared = %d\n\n", nShared);
   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel copyin(nThreadPrivate) private(nPrivate) shared(nShared) firstprivate(nFirstPrivate)
   {
      #pragma omp for schedule(static) lastprivate(nLastPrivate)
      for (i = 0 ; i < NUM_THREADS ; ++i) {
         for (j = 0 ; j < NUM_LOOPS ; ++j) {
            int nThread = omp_get_thread_num();
            assert(nThread < NUM_THREADS);

            if (nThread == SLEEP_THREAD)
               Sleep(100);
            nSave[nThread][ThreadPrivate][j] = nThreadPrivate;
            nSave[nThread][Private][j] = nPrivate;
            nSave[nThread][Shared][j] = nShared;
            nSave[nThread][FirstPrivate][j] = nFirstPrivate;
            nSave[nThread][LastPrivate][j] = nLastPrivate;
            nThreadPrivate = nThread;
            nPrivate = nThread;
            nShared = nThread;
            nLastPrivate = nThread;
            --nFirstPrivate;
         }
      }
   }

   for (i = 0 ; i < NUM_LOOPS ; ++i) {
      for (j = 0 ; j < NUM_THREADS ; ++j) {
         printf_s("These are the variables at entry of "
                  "loop %d of thread %d.\n", i + 1, j);
         printf_s("nThreadPrivate = %d\n",
                  nSave[j][ThreadPrivate][i]);
         printf_s("      nPrivate = %d\n",
                  nSave[j][Private][i]);
         printf_s(" nFirstPrivate = %d\n",
                  nSave[j][FirstPrivate][i]);
         printf_s("  nLastPrivate = %d\n",
                  nSave[j][LastPrivate][i]);
         printf_s("       nShared = %d\n\n",
                  nSave[j][Shared][i]);
      }
   }

   printf_s("These are the variables after exit from "
            "the parallel region.\n");
   printf_s("nThreadPrivate = %d (The last value in the "
            "master thread)\n", nThreadPrivate);
   printf_s("      nPrivate = %d (The value prior to "
            "entering parallel region)\n", nPrivate);
   printf_s(" nFirstPrivate = %d (The value prior to "
            "entering parallel region)\n", nFirstPrivate);
   printf_s("  nLastPrivate = %d (The value from the "
            "last iteration of the loop)\n", nLastPrivate);
   printf_s("       nShared = %d (The value assigned, "
            "from the delayed thread, %d)\n\n",
            nShared, SLEEP_THREAD);
}
```

```Output
These are the variables before entry into the parallel region.
nThreadPrivate = 4
      nPrivate = 4
nFirstPrivate = 4
  nLastPrivate = 4
       nShared = 4

These are the variables at entry of loop 1 of thread 0.
nThreadPrivate = 4
      nPrivate = 1310720
nFirstPrivate = 4
  nLastPrivate = 1245104
       nShared = 3

These are the variables at entry of loop 1 of thread 1.
nThreadPrivate = 4
      nPrivate = 4488
nFirstPrivate = 4
  nLastPrivate = 19748
       nShared = 0

These are the variables at entry of loop 1 of thread 2.
nThreadPrivate = 4
      nPrivate = -132514848
nFirstPrivate = 4
  nLastPrivate = -513199792
       nShared = 4

These are the variables at entry of loop 1 of thread 3.
nThreadPrivate = 4
      nPrivate = 1206
nFirstPrivate = 4
  nLastPrivate = 1204
       nShared = 2

These are the variables at entry of loop 2 of thread 0.
nThreadPrivate = 0
      nPrivate = 0
nFirstPrivate = 3
  nLastPrivate = 0
       nShared = 0

These are the variables at entry of loop 2 of thread 1.
nThreadPrivate = 1
      nPrivate = 1
nFirstPrivate = 3
  nLastPrivate = 1
       nShared = 1

These are the variables at entry of loop 2 of thread 2.
nThreadPrivate = 2
      nPrivate = 2
nFirstPrivate = 3
  nLastPrivate = 2
       nShared = 2

These are the variables at entry of loop 2 of thread 3.
nThreadPrivate = 3
      nPrivate = 3
nFirstPrivate = 3
  nLastPrivate = 3
       nShared = 3

These are the variables after exit from the parallel region.
nThreadPrivate = 0 (The last value in the master thread)
      nPrivate = 4 (The value prior to entering parallel region)
nFirstPrivate = 4 (The value prior to entering parallel region)
  nLastPrivate = 3 (The value from the last iteration of the loop)
       nShared = 1 (The value assigned, from the delayed thread, 1)
```

## <a name="reduction"></a>Reduzierung

Gibt an, dass eine oder mehrere Variablen, die für jeden Thread privat sind ein Reduzierungsvorgang am Ende des parallelen Bereichs werden.

```
reduction(operation:var)
```

### <a name="parameters"></a>Parameter

*operation*<br/>
Der Operator für den Vorgang auf die Variablen *Var* am Ende des parallelen Bereichs.

*var*<br/>
Eine oder mehrere Variablen, auf denen Sie skalare Reduzierung. Wenn mehr als eine Variable angegeben ist, trennen Sie Namen durch ein Komma.

### <a name="remarks"></a>Hinweise

`reduction` gilt für die folgenden Anweisungen:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)

Weitere Informationen finden Sie unter [2.7.2.6 Verringerung](../../../parallel/openmp/2-7-2-6-reduction.md).

### <a name="example"></a>Beispiel

```cpp
// omp_reduction.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define SUM_START   1
#define SUM_END     10
#define FUNC_RETS   {1, 1, 1, 1, 1}

int bRets[5] = FUNC_RETS;
int nSumCalc = ((SUM_START + SUM_END) * (SUM_END - SUM_START + 1)) / 2;

int func1( ) {return bRets[0];}
int func2( ) {return bRets[1];}
int func3( ) {return bRets[2];}
int func4( ) {return bRets[3];}
int func5( ) {return bRets[4];}

int main( )
{
    int nRet = 0,
        nCount = 0,
        nSum = 0,
        i,
        bSucceed = 1;

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel reduction(+ : nCount)
    {
        nCount += 1;

        #pragma omp for reduction(+ : nSum)
        for (i = SUM_START ; i <= SUM_END ; ++i)
            nSum += i;

        #pragma omp sections reduction(&& : bSucceed)
        {
            #pragma omp section
            {
                bSucceed = bSucceed && func1( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func2( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func3( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func4( );
            }

            #pragma omp section
            {
                bSucceed = bSucceed && func5( );
            }
        }
    }

    printf_s("The parallel section was executed %d times "
             "in parallel.\n", nCount);
    printf_s("The sum of the consecutive integers from "
             "%d to %d, is %d\n", 1, 10, nSum);

    if (bSucceed)
        printf_s("All of the functions, func1 through "
                 "func5 succeeded!\n");
    else
        printf_s("One or more of the functions, func1 "
                 "through func5 failed!\n");

    if (nCount != NUM_THREADS)
    {
        printf_s("ERROR: For %d threads, %d were counted!\n",
                 NUM_THREADS, nCount);
        nRet |= 0x1;
   }

    if (nSum != nSumCalc)
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                "but %d was reported!\n",
                SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x10;
    }

    if (bSucceed != (bRets[0] && bRets[1] &&
                     bRets[2] && bRets[3] && bRets[4]))
    {
        printf_s("ERROR: The sum of %d through %d should be %d, "
                 "but %d was reported!\n",
                 SUM_START, SUM_END, nSumCalc, nSum);
        nRet |= 0x100;
    }
}
```

```Output
The parallel section was executed 4 times in parallel.
The sum of the consecutive integers from 1 to 10, is 55
All of the functions, func1 through func5 succeeded!
```

## <a name="schedule"></a>Zeitplan

Gilt für die [für](openmp-directives.md#for-openmp) Richtlinie.

```
schedule(type[,size])
```

### <a name="parameters"></a>Parameter

*Typ*<br/>
Die Art der Planung, entweder `dynamic`, `guided`, `runtime`, oder `static`.

*size*<br/>
(Optional) Gibt die Größe der Iterationen. *Größe* muss eine ganze Zahl sein. Nicht gültig, wenn *Typ* ist `runtime`.

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [2.4.1 for-Konstrukt](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_schedule.cpp
// compile with: /openmp
#include <windows.h>
#include <stdio.h>
#include <omp.h>

#define NUM_THREADS 4
#define STATIC_CHUNK 5
#define DYNAMIC_CHUNK 5
#define NUM_LOOPS 20
#define SLEEP_EVERY_N 3

int main( )
{
    int nStatic1[NUM_LOOPS],
        nStaticN[NUM_LOOPS];
    int nDynamic1[NUM_LOOPS],
        nDynamicN[NUM_LOOPS];
    int nGuided[NUM_LOOPS];

    omp_set_num_threads(NUM_THREADS);

    #pragma omp parallel
    {
        #pragma omp for schedule(static, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStatic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(static, STATIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nStaticN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, 1)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamic1[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(dynamic, DYNAMIC_CHUNK)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nDynamicN[i] = omp_get_thread_num( );
        }

        #pragma omp for schedule(guided)
        for (int i = 0 ; i < NUM_LOOPS ; ++i)
        {
            if ((i % SLEEP_EVERY_N) == 0)
                Sleep(0);
            nGuided[i] = omp_get_thread_num( );
        }
    }

    printf_s("------------------------------------------------\n");
    printf_s("| static | static | dynamic | dynamic | guided |\n");
    printf_s("|    1   |    %d   |    1    |    %d    |        |\n",
             STATIC_CHUNK, DYNAMIC_CHUNK);
    printf_s("------------------------------------------------\n");

    for (int i=0; i<NUM_LOOPS; ++i)
    {
        printf_s("|    %d   |    %d   |    %d    |    %d    |"
                 "    %d   |\n",
                 nStatic1[i], nStaticN[i],
                 nDynamic1[i], nDynamicN[i], nGuided[i]);
    }

    printf_s("------------------------------------------------\n");
}
```

```Output
------------------------------------------------
| static | static | dynamic | dynamic | guided |
|    1   |    5   |    1    |    5    |        |
------------------------------------------------
|    0   |    0   |    0    |    2    |    1   |
|    1   |    0   |    3    |    2    |    1   |
|    2   |    0   |    3    |    2    |    1   |
|    3   |    0   |    3    |    2    |    1   |
|    0   |    0   |    2    |    2    |    1   |
|    1   |    1   |    2    |    3    |    3   |
|    2   |    1   |    2    |    3    |    3   |
|    3   |    1   |    0    |    3    |    3   |
|    0   |    1   |    0    |    3    |    3   |
|    1   |    1   |    0    |    3    |    2   |
|    2   |    2   |    1    |    0    |    2   |
|    3   |    2   |    1    |    0    |    2   |
|    0   |    2   |    1    |    0    |    3   |
|    1   |    2   |    2    |    0    |    3   |
|    2   |    2   |    2    |    0    |    0   |
|    3   |    3   |    2    |    1    |    0   |
|    0   |    3   |    3    |    1    |    1   |
|    1   |    3   |    3    |    1    |    1   |
|    2   |    3   |    3    |    1    |    1   |
|    3   |    3   |    0    |    1    |    3   |
------------------------------------------------
```

## <a name="shared-openmp"></a>shared

Gibt an, dass eine oder mehrere Variablen, die auf allen Threads freigegeben werden soll.

```
shared(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Eine oder mehrere Variablen freigeben. Wenn mehr als eine Variable angegeben ist, trennen Sie Namen durch ein Komma.

### <a name="remarks"></a>Hinweise

Eine weitere Möglichkeit zum Teilen von Variablen zwischen Threads ist mit der [Copyprivate](#copyprivate) Klausel.

`shared` gilt für die folgenden Anweisungen:

- [parallel](openmp-directives.md#parallel)
- [for](openmp-directives.md#for-openmp)
- [Abschnitte](openmp-directives.md#sections-openmp)

Weitere Informationen finden Sie unter [2.7.2.4 freigegebene](../../../parallel/openmp/2-7-2-4-shared.md).

### <a name="example"></a>Beispiel

Finden Sie unter [private](#private-openmp) ein Beispiel der Verwendung von `shared`.
