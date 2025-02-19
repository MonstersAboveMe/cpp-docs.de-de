---
title: task-Klasse (Concurrency Runtime)
ms.date: 11/04/2016
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: 99676ac0fff9584cd8453562f8918f6cadd66666
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385205"
---
# <a name="task-class-concurrency-runtime"></a>task-Klasse (Concurrency Runtime)

Die Parallel Patterns Library (PPL) `task`-Klasse. Ein `task`-Objekt stellt Arbeit dar, die asynchron und übereinstimmend mit anderen Tasks und paralleler Arbeit , die von parallelen Algorithmen in der Concurrency Runtime erzeugt wird, ausgeführt werden kann. Es enthält bei erfolgreichem Abschluss ein Ergebnis vom Typ `_ResultType`. Tasks des Typs `task<void>` führen zu keinem Ergebnis. Eine Aufgabe kann erwartet und unabhängig von anderen Aufgaben abgebrochen werden. Sie können auch mit anderen Aufgaben, die mithilfe von Fortsetzungen, bestehen ( `then`), und verbinden ( `when_all`) und Auswahl ( `when_any`) Muster.

## <a name="syntax"></a>Syntax

```
template <typename T>
class task;

template <>
class task<void>;

template<typename _ReturnType>
class task;
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Task-Objekt.

*_ReturnType*<br/>
Der Ergebnistyp dieses Tasks.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|Beschreibung|
|----------|-----------------|
|`result_type`|Der Typ des von einem Objekt dieser Klasse erstellten Ergebnisses.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[task](#ctor)|Überladen. Erstellt ein `task`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[get](#get)|Überladen. Gibt das von diesem Task erstellte Ergebnis zurück. Wenn sich die Aufgabe nicht in einem abschließenden Zustand befindet, wird mit dem `get`-Aufruf gewartet, bis die Aufgabe fertig gestellt wurde. Diese Methode gibt bei dem Aufruf einer Aufgabe mit einem `result_type` von `void` keinen Wert zurück.|
|[is_apartment_aware](#is_apartment_aware)|Bestimmt, ob der Task eine `IAsyncInfo`-Schnittstelle der Windows Runtime entpackt oder von einem solchen Task abgeleitet wurde.|
|[is_done](#is_done)|Bestimmt, ob die Aufgabe abgeschlossen wurde.|
|[scheduler](#scheduler)|Gibt den Planer für diesen Task zurück.|
|[then](#then)|Überladen. Fügt diesem Task einen Fortsetzungstask hinzu.|
|[wait](#wait)|Erwartet, dass dieser Task einen Terminalzustand erreicht. Es ist möglich, dass das `wait`-Element den Task inline ausführt, wenn alle Taskabhängigkeiten erfüllt sind und er nicht bereits zur Ausführung durch einen Hintergrundworker aufgehoben wurde.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[Operator!=](#operator_neq)|Überladen. Bestimmt, ob zwei `task`-Objekte unterschiedliche interne Aufgaben darstellen.|
|[operator=](#operator_eq)|Überladen. Ersetzt den Inhalt eines `task`-Objekts durch einen anderen.|
|[operator==](#operator_eq_eq)|Überladen. Bestimmt, ob zwei `task`-Objekte die gleiche interne Aufgabe darstellen.|

## <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie unter [Aufgabenparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`task`

## <a name="requirements"></a>Anforderungen

**Header:** ppltasks.h

**Namespace:** Parallelität

##  <a name="get"></a> Erhalten

Gibt das von diesem Task erstellte Ergebnis zurück. Wenn sich die Aufgabe nicht in einem abschließenden Zustand befindet, wird mit dem `get`-Aufruf gewartet, bis die Aufgabe fertig gestellt wurde. Diese Methode gibt bei dem Aufruf einer Aufgabe mit einem `result_type` von `void` keinen Wert zurück.

```
_ReturnType get() const;

void get() const;
```

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Aufgabe.

### <a name="remarks"></a>Hinweise

Wenn die Aufgabe abgebrochen wird, einen Aufruf von `get` löst eine [Task_canceled](task-canceled-class.md) Ausnahme. Wenn die Aufgabe eine Ausnahme während der Ausführung feststellt oder an sie eine Ausnahme aus einer vorherigen Aufgabe weitergegeben wurde, löst ein Aufruf von `get` diese Ausnahme aus.

> [!IMPORTANT]
>  Rufen Sie in einer app (Universelle Windows Plattform) nicht [Concurrency:: Task::](#wait) oder `get` ( `wait` Aufrufe `get`) im Code, der auf dem UI-Thread ausgeführt wird. Andernfalls löst die Laufzeit [invalid_operation](invalid-operation-class.md) daran, dass diese Methoden den aktuellen Thread blockieren, und dazu führen, die app dass kann reagiert. Sie können jedoch die `get`-Methode aufrufen, um das Ergebnis der vorangegangenen Aufgabe in einer aufgabenbasierten Fortsetzung zu erhalten, da das Ergebnis sofort verfügbar ist.

##  <a name="is_apartment_aware"></a> is_apartment_aware

Bestimmt, ob der Task eine `IAsyncInfo`-Schnittstelle der Windows Runtime entpackt oder von einem solchen Task abgeleitet wurde.

```
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Rückgabewert

**"true"** , wenn die Aufgabe entpackt ein `IAsyncInfo` -Schnittstelle oder von einer solchen Aufgabe abgeleitet wird **"false"** andernfalls.

##  <a name="is_done"></a>  Task:: is_done-Methode (Concurrency Runtime)

Bestimmt, ob die Aufgabe abgeschlossen wurde.

```
bool is_done() const;
```

### <a name="return-value"></a>Rückgabewert

"True", wenn die Aufgabe abgeschlossen wurde, andernfalls "false".

### <a name="remarks"></a>Hinweise

Die Funktion gibt "true" zurück, wenn die Aufgabe abgeschlossen oder abgebrochen wurde (mit oder ohne Benutzerausnahme).

##  <a name="operator_neq"></a> Operator! =

Bestimmt, ob zwei `task`-Objekte unterschiedliche interne Aufgaben darstellen.

```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die Aufgabe, die verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**"true"** Wenn die Objekte auf unterschiedliche zugrunde liegenden Aufgaben beziehen und **"false"** andernfalls.

##  <a name="operator_eq"></a> operator=

Ersetzt den Inhalt eines `task`-Objekts durch einen anderen.

```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parameter

*_Other*<br/>
Das `task`-Quellobjekt.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Hinweise

Da sich `task` wie ein intelligenter Zeiger verhält, stellt dieses `task`-Objekt nach einer Kopierzuweisung die gleiche Aufgabe dar wie `_Other`.

##  <a name="operator_eq_eq"></a> Operator ==

Bestimmt, ob zwei `task`-Objekte die gleiche interne Aufgabe darstellen.

```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parameter

*_Rhs*<br/>
Die Aufgabe, die verglichen werden soll.

### <a name="return-value"></a>Rückgabewert

**"true"** , wenn die Objekte auf die gleiche zugrunde liegende Aufgabe verweisen und **"false"** andernfalls.

##  <a name="scheduler"></a>  Task:: Scheduler-Methode (Concurrency Runtime)

Gibt den Planer für diesen Task zurück.

```
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Planer.

##  <a name="ctor"></a> Aufgabe

Erstellt ein `task`-Objekt.

```
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Parameters, von dem die Aufgabe erstellt werden soll.

*_Param*<br/>
Der Parameter, von dem der Task erstellt werden soll. Ist dies möglicherweise einen Lambda-Ausdruck, der ein Funktionsobjekt, einem `task_completion_event<result_type>` Objekt oder eine iasyncinfo, wenn Sie Aufgaben in Ihrer Windows-Runtime-app verwenden. Lambda-Ausdrucks oder Funktion muss ein Typ wie `std::function<X(void)>`, wobei X eine Variable des Typs sein kann `result_type`, `task<result_type>`, oder eine iasyncinfo in Windows-Runtime-apps.

*_TaskOptions*<br/>
Die Aufgabenoptionen enthalten Abbruchtoken, Planer usw.

*_Other*<br/>
Das `task`-Quellobjekt.

### <a name="remarks"></a>Hinweise

Der Standardkonstruktor für `task` ist nur vorhanden, damit Aufgaben in Containern verwendet werden können. Eine erstellte Standardaufgabe kann nicht verwendet werden, bis Sie ihr eine gültige Aufgabe zuweisen. Methoden, z. B. `get`, `wait` oder `then` löst eine [Invalid_argument](../../../standard-library/invalid-argument-class.md) Ausnahme aus, wenn für eine erstellte Standardaufgabe aufgerufen.

Eine Aufgabe, die aus einem `task_completion_event` erstellt wird, wird abgeschlossen (und danach werden ihre Fortsetzungen geplant), wenn das Aufgabenabschlussereignis festgelegt ist.

Die Version des Konstruktors, die ein Abbruchtoken verwendet, erstellt eine Aufgabe, die mithilfe der `cancellation_token_source`, aus der das Token abgerufen wurde, abgebrochen werden kann. Die Aufgaben, die ohne ein Abbruchtoken erstellt werden, können nicht abgebrochen werden.

Die Aufgaben, die aus einer `Windows::Foundation::IAsyncInfo`-Schnittstelle oder einem Lambda-Ausdruck erstellt werden, der eine `IAsyncInfo`-Schnittstelle zurückgibt, erreichen den abgeschlossenen Zustand, wenn der enthaltene asynchrone Windows-Runtime-Vorgang oder die enthaltene Aktion abgeschlossen wurde. In ähnlicher Weise erreichen Aufgaben, die aus einem Lambda-Ausdruck erstellt werden, der einen `task<result_type>` zurückgibt, den abgeschlossenen Zustand, wenn die innere Aufgabe den abgeschlossenen Zustand erreicht, und nicht wenn die Rückgabe vom Lambda-Ausdruck erfolgt.

`task` verhält sich wie ein intelligenter Zeiger und kann mehrmals als Wert übergeben werden. Ein Zugriff ist durch mehrere Threads ohne Sperren möglich.

Konstruktorüberladungen, die eine iasyncinfo-Schnittstelle oder einen Lambda-Ausdruck, der eine solche Schnittstelle zurückgibt, sind nur für Windows-Runtime-apps verfügbar.

Weitere Informationen finden Sie unter [Aufgabenparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="then"></a> Klicken Sie dann

Fügt diesem Task einen Fortsetzungstask hinzu.

```
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```

### <a name="parameters"></a>Parameter

*_Function*<br/>
Der Typ des Funktionsobjekts, das von dieser Aufgabe aufgerufen wird.

*_Func*<br/>
Die Fortsetzungsfunktion, die ausgeführt werden soll, wenn diese Aufgabe abgeschlossen ist. Diese Fortsetzungsfunktion muss als Eingabe die Variable `result_type` oder `task<result_type>` verwenden, wobei `result_type` der Ergebnistyp ist, den diese Aufgabe erzeugt.

*_TaskOptions*<br/>
Die Aufgabenoptionen umfassen das Abbruchtoken, den Planer und den Fortsetzungskontext. Standardmäßig werden die vorherigen drei Optionen von der Vorgängeraufgabe geerbt.

*_CancellationToken*<br/>
Das Abbruchtoken, das der Fortsetzungsaufgabe zugeordnet werden soll. Eine Fortsetzungsaufgabe, die ohne ein Abbruchtoken erstellt wird, erbt das Token von der Vorgängeraufgabe.

*_ContinuationContext*<br/>
Eine Variable, die angibt, wo die Fortsetzung ausgeführt werden soll. Diese Variable ist nur nützlich, wenn in einer UWP-app verwendet. Weitere Informationen finden Sie unter [Task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Rückgabewert

Die neu erstellte Fortsetzungsaufgabe. Der Ergebnistyp der zurückgegebenen Aufgabe wird von dem bestimmt, was `_Func` zurückgibt.

### <a name="remarks"></a>Hinweise

Die Überladungen der `then` , dass ein Lambda oder Funktionselement ist, eine iasyncinfo-Schnittstelle zurückgibt, sind nur für Windows-Runtime-apps verfügbar.

Weitere Informationen zur Verwendung von aufgabenfortsetzungen für asynchrone Aufgaben finden Sie unter [Aufgabenparallelität](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="wait"></a> Warte

Erwartet, dass dieser Task einen Terminalzustand erreicht. Es ist möglich, dass das `wait`-Element den Task inline ausführt, wenn alle Taskabhängigkeiten erfüllt sind und er nicht bereits zur Ausführung durch einen Hintergrundworker aufgehoben wurde.

```
task_status wait() const;
```

### <a name="return-value"></a>Rückgabewert

Ein `task_status`-Wert, der entweder `completed` oder `canceled` ist. Wenn die Aufgabe eine Ausnahme während der Ausführung feststellt oder an sie eine Ausnahme aus einer vorherigen Aufgabe weitergegeben wurde, löst `wait` diese Ausnahme aus.

### <a name="remarks"></a>Hinweise

> [!IMPORTANT]
>  Rufen Sie in einer app (Universelle Windows Plattform) nicht `wait` im Code, der auf dem UI-Thread ausgeführt wird. Andernfalls löst die Laufzeit [concurrency::invalid_operation](invalid-operation-class.md) aus, da diese Methode den aktuellen Thread blockiert und die App dadurch möglicherweise nicht mehr reagiert. Sie können jedoch die [concurrency::task::get](#get) -Methode aufrufen, um das Ergebnis der Vorgängeraufgabe in einer aufgabenbasierten Fortsetzung zu erhalten.

## <a name="see-also"></a>Siehe auch

[Concurrency-Namespace](concurrency-namespace.md)
