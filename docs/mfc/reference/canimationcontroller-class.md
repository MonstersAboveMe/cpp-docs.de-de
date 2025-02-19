---
title: CAnimationController-Klasse
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: a3a533b876b9ca245c0553c4c24a815ef3cabca1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151187"
---
# <a name="canimationcontroller-class"></a>CAnimationController-Klasse

Implementiert den Animationscontroller, der eine zentrale Schnittstelle zum Erstellen und Verwalten von Animationen bereitstellt.

## <a name="syntax"></a>Syntax

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Erstellt einen Animationscontroller.|
|[CAnimationController::~CAnimationController](#_dtorcanimationcontroller)|Der Destruktor. Wird aufgerufen, wenn Animation-Controller-Objekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Fügt ein Animationsobjekt zu einer Gruppe, die den Animationscontroller angehört.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Fügt einen Keyframe Gruppe hinzu.|
|[CAnimationController::AnimateGroup](#animategroup)|Bereitet eine Gruppe zum Ausführen von Animationen und plant diese optional.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Überladen. Wird aufgerufen, durch das Framework zum Bereinigen der Gruppe, wenn die Animation geplant wurde.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Überladen. Erstellt einen Keyframe, der vom Übergang abhängig ist, und fügt ihn der angegebenen Gruppe hinzu.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Legt fest oder gibt einen Handler aufrufen, wenn der Animations-Manager-Status ändert.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Legt fest oder gibt einen Handler für Ereignisse zu abfrageantwortzeiten und Handler für das Zeitsteuerungssystem Updates frei.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Legt fest oder gibt die Priorität Vergleich-Handler, der aufgerufen wird, um festzustellen, ob ein geplantes Storyboard abgebrochen, führten zu dem Schluss, abgeschnitten oder komprimiert werden kann.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Legt fest oder gibt einen Handler für die Storyboard-Status "und" Update-Ereignisse.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Überladen. Sucht nach einer Animationsgruppe durch das Storyboard.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Sucht, die eine Variable angegebene Animation "Animation"-Objekts an.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Gibt einen Keyframe, der Anfang des Storyboards identifiziert.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Bietet Zugriff auf gekapselte IUIAnimationManager-Objekt.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Bietet Zugriff auf gekapselte IUIAnimationTimer-Objekt.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Ein Zeiger auf IUIAnimationTransitionFactory-Schnittstelle oder NULL, wenn Fehler bei der Erstellung der Übergangsbibliothek.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Bietet Zugriff auf gekapselte IUIAnimationTransitionLibrary-Objekt.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Erfahren Sie, ob mindestens eine Gruppe Animation wiedergegeben wird.|
|[CAnimationController::IsValid](#isvalid)|Erfahren Sie, ob Animationscontroller gültig ist.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Wird von Framework aufgerufen, wenn es sich bei ganzzahligen Wert der Animationsvariablen geändert hat.|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|Wird aufgerufen, durch das Framework als Reaktion auf StatusChanged-Ereignis von der Animations-Manager.|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|Vom Framework aufgerufen, nachdem ein Animationsupdate abgeschlossen ist.|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|Wird vom Framework aufgerufen, bevor ein Animationsupdate beginnt.|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Vom Framework aufgerufen, wenn eine minimale wünschenswert Framerate die Rendering-Framerate für eine Animation unterschreitet.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Vom Framework aufgerufen, wenn der Wert der Animationsvariablen geändert hat.|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Vom Framework aufgerufen, rechts, bevor die Animation geplant wird.|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Vom Framework aufgerufen, wenn die Storyboardstatus geändert hat.|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|Vom Framework aufgerufen, wenn ein Storyboard aktualisiert wurde.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Entfernt alle Animationsgruppen aus Animationscontroller.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Entfernt eine Animationsgruppe mit der angegebenen ID aus Animationscontroller an.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Entfernen Sie ein Animationsobjekt aus Animationscontroller an.|
|[CAnimationController::RemoveTransitions](#removetransitions)|Entfernt Übergänge von Animationsobjekten, die der angegebenen Gruppe gehören.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Plant eine Animation.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Legt eine Beziehung zwischen den Animationscontroller und ein Fenster.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Leitet die Animations-Manager zum Aktualisieren der Werte aller Variablen der Animation an.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Überladen. Ein Hilfsprogramm, der die Gruppe bereinigt.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Vom Framework aufgerufen, wenn eine Animation für die angegebene Gruppe lediglich geplant wurde.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Ein Keyframe, der Anfang des Storyboards darstellt.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Gibt an, ob als Animationscontroller gültig oder nicht ist. Dieser Member ist auf "false" festgelegt, wenn das aktuelle Betriebssystem Windows Animations-API nicht unterstützt.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Eine Liste der Animationsgruppen, die an diesen Animationscontroller gehören.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Speichert einen Zeiger auf Animations-Manager-COM-Objekt.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Speichert einen Zeiger auf Animation Timer COM-Objekt.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Ein Zeiger auf ein verknüpftes CWnd-Objekt, das automatisch neu gezeichnet werden kann, wenn der Status der Animations-Manager geändert wurde oder Ereignis nach dem Update aufgetreten. NULL kann sein.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Speichert einen Zeiger auf Übergang Factory COM-Objekt.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Speichert einen Zeiger auf Übergang Bibliothek COM-Objekt.|

## <a name="remarks"></a>Hinweise

CAnimationController-Klasse ist die wichtigste Klasse, die Animationen verwaltet. Sie können eine oder mehrere Instanzen von Animationscontroller in einer Anwendung erstellt und optional eine Instanz von Animationscontroller an ein CWnd-Objekt, das mit CAnimationController:: SetRelatedWnd herstellen. Diese Verbindung ist erforderlich, zum Senden von WM_PAINT-Meldungen an das verknüpfte Fenster automatisch beim Animation-Manager-Status sich geändert hat oder Animationszeitgeber wurde aktualisiert. Wenn Sie diese Beziehung nicht aktivieren, müssen Sie ein Fenster neu gezeichnet werden, die eine Animation manuell anzeigt. Zu diesem Zweck können Sie CAnimationController eine Klasse ableiten und OnAnimationManagerStatusChanged und/oder OnAnimationTimerPostUpdate überschreiben und eine oder mehrere Windows bei Bedarf ungültig.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>  CAnimationController:: ~ CAnimationController

Der Destruktor. Wird aufgerufen, wenn Animation-Controller-Objekt zerstört wird.

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>  CAnimationController:: AddAnimationObject

Fügt ein Animationsobjekt zu einer Gruppe, die den Animationscontroller angehört.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parameter

*pObject*<br/>
Ein Zeiger auf ein Animationsobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den vorhandenen oder neuen Animationsgruppe, in denen pObject hinzugefügt wurde, wenn die Funktion erfolgreich ausgeführt wird; NULL, wenn pObject bereits zu einer Gruppe hinzugefügt wurde, die zu einer anderen Animationscontroller gehört.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Methode, um den Animationscontroller ein Animationsobjekt hinzufügen. Ein Objekt wird eine Gruppe anhand des Objekts GroupID hinzugefügt (Siehe CAnimationBaseObject:: SetID). Der Animationscontroller wird eine neue Gruppe erstellen, ist dies das erste Objekt, das der angegebenen GroupID hinzugefügt wird. Ein Animationsobjekt kann nur eine einzige Animation-Controller hinzugefügt werden. Wenn Sie ein Objekt an einen anderen Controller hinzufügen möchten, rufen Sie zuerst die RemoveAnimationObject. Wenn Sie SetID mit neuen GroupID für ein Objekt, die bereits zu einer Gruppe hinzugefügt wurde aufrufen, wird das Objekt aus der alten Gruppe entfernt und hinzugefügt werden zu einer anderen Gruppe mit der angegebenen ID.

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

Fügt einen Keyframe Gruppe hinzu.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID.

*pKeyframe*<br/>
Ein Zeiger auf einen Keyframe.

### <a name="return-value"></a>Rückgabewert

True, wenn die Funktion erfolgreich ist. andernfalls "false".

### <a name="remarks"></a>Hinweise

In der Regel müssen Sie diese Methode aufzurufen, verwenden stattdessen Aufrufen die erstellt und fügt automatisch den erstellte Keyframe zu einer Gruppe hinzu.

##  <a name="animategroup"></a>  CAnimationController:: AnimateGroup

Bereitet eine Gruppe zum Ausführen von Animationen und plant diese optional.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*bScheduleNow*<br/>
Gibt an, ob die Animation sofort ausgeführt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Animation wurde erfolgreich geplant und ausgeführt wurde.

### <a name="remarks"></a>Hinweise

Diese Methode führt die eigentliche Arbeit Storyboard erstellen, Hinzufügen von Animationsvariablen, Anwenden von Übergängen und Keyframes festlegen. Es ist möglich, verzögern, planen, wenn Sie bScheduleNow auf "false" festlegen. In diesem Fall wird die angegebene Gruppe ein Storyboard, das für die Animation eingerichtet wurde. An diesem Punkt können Sie Ereignisse für die Variablen Storyboard und Animationen einrichten. Wenn Sie tatsächlich müssen zum Ausführen des Animation Aufrufs CAnimationController:: ScheduleGroup auf.

##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController

Erstellt einen Animationscontroller.

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup

Wird aufgerufen, durch das Framework zum Bereinigen der Gruppe, wenn die Animation geplant wurde.

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*pGroup*<br/>
Ein Zeiger auf die Animation aus, zu bereinigen.

### <a name="remarks"></a>Hinweise

Diese Methode entfernt alle Übergänge und Keyframes aus der angegebenen Gruppe ist, da sie nicht relevant sind, nachdem eine Animation geplant wurde.

##  <a name="createkeyframe"></a>  Aufrufen

Erstellt einen Keyframe, der vom Übergang abhängig ist, und fügt ihn der angegebenen Gruppe hinzu.

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die ID der Gruppe an, für die der Keyframe erstellt wird.

*pTransition*<br/>
Ein Zeiger auf den Übergang. Der Keyframe wird nach diesem Übergang in das Storyboard eingefügt.

*pKeyframe*<br/>
Ein Zeiger auf das Basiskeyframe für diesen Keyframe.

*offset*<br/>
Offset in Sekunden gegenüber dem vom „pKeyframe“ angegebenen Basiskeyframe.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Keyframe, wenn die Funktion erfolgreich ausgeführt wurde.

### <a name="remarks"></a>Hinweise

Sie können den zurückgegebenen Zeiger speichern und weitere Keyframes auf dem neu erstellten Keyframe basieren lassen (siehe dazu die zweite Überladung). Es ist möglich, Übergänge an Keyframes zu beginnen – siehe dazu „CBaseTransition::SetKeyframes“. In dieser Weise erstellte Keyframes müssen nicht gelöscht werden, da sie von Animationsgruppen automatisch gelöscht werden. Gehen Sie beim Erstellen von Keyframes auf der Basis anderer Keyframes und Übergänge umsichtig vor, und vermeiden Sie Zirkelbezüge.

##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent

Legt fest oder gibt einen Handler aufrufen, wenn der Animations-Manager-Status ändert.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob festgelegt oder einen Handler aufgehoben werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Handler wurde erfolgreich festgelegt oder freigegeben wurde.

### <a name="remarks"></a>Hinweise

Wenn ein Handler (aktiviert) festgelegt ist ruft Windows Animation OnAnimationManagerStatusChanged aus, wenn Animations-Manager-Status ändert.

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController:: EnableAnimationTimerEventHandler

Legt fest oder gibt einen Handler für Ereignisse zu abfrageantwortzeiten und Handler für das Zeitsteuerungssystem Updates frei.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob festgelegt oder die Handler aufgehoben werden soll.

*idleBehavior*<br/>
Gibt die leerlaufverhalten für Timer-updatehandler an.

### <a name="return-value"></a>Rückgabewert

True, wenn der Handler wurde erfolgreich festgelegt oder freigegeben wurden. FALSE, wenn diese Methode wird ein zweites Mal aufgerufen, ohne die Handler zuerst freizugeben, oder wenn ein anderer Fehler auftritt.

### <a name="remarks"></a>Hinweise

Wenn der Handler (aktiviert) Windows Animations-API-Aufrufe OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow Methoden festgelegt sind. In diesem Fall müssen Sie eine Animation Timer Animations-API von Windows Update-Storyboards zu aktivieren. Andernfalls müssen Sie CAnimationController::UpdateAnimationManager aufrufen, um die Animation direkte Manager zum Aktualisieren der Werte aller Variablen der Animation.

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController:: EnablePriorityComparisonHandler aktivieren

Legt fest oder gibt die Priorität Vergleich-Handler, der aufgerufen wird, um festzustellen, ob ein geplantes Storyboard abgebrochen, führten zu dem Schluss, abgeschnitten oder komprimiert werden kann.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parameter

*dwHandlerType*<br/>
Eine Kombination von UI_ANIMATION_PHT_ kennzeichnet (siehe "Hinweise"), der angibt, welche Handler festgelegt oder aufgehoben.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Handler wurde erfolgreich festgelegt oder freigegeben wurde.

### <a name="remarks"></a>Hinweise

Wenn ein Handler für Windows-Animation Aufrufe für die Gruppe (aktiviert) die folgenden virtuellen Methoden je nach dwHandlerType auf ist: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. DwHandler kann es sich um eine Kombination der folgenden Flags sein: UI_ANIMATION_PHT_NONE - Version alle Handler UI_ANIMATION_PHT_CANCEL - legen Sie "Abbrechen" Vergleich-Handler UI_ANIMATION_PHT_CONCLUDE - festgelegt Conclude Vergleich Handler UI_ANIMATION_PHT_COMPRESS – Festlegen der komprimieren Vergleich Handler UI_ANIMATION_PHT_TRIM: festgelegt Trim-Vergleich Handler UI_ANIMATION_PHT_CANCEL_REMOVE – entfernen Sie "Abbrechen" Vergleich Handler UI_ANIMATION_PHT_CONCLUDE_REMOVE - Remove Conclude Vergleich Handler UI_ANIMATION_PHT_COMPRESS_REMOVE - komprimieren Vergleich Handler UI_ANIMATION_PHT entfernen _TRIM_REMOVE – Entfernen eines Handlers kürzen Vergleich

##  <a name="enablestoryboardeventhandler"></a>  CAnimationController:: EnableStoryboardEventHandler

Legt fest oder gibt einen Handler für die Storyboard-Status "und" Update-Ereignisse.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID.

*bEnable*<br/>
Gibt an, ob festgelegt oder einen Handler aufgehoben werden soll.

### <a name="return-value"></a>Rückgabewert

True, wenn der Handler wurde erfolgreich festgelegt oder freigegeben wurde. "False", wenn der Gruppe "angegebene Animation" sich jetzt befindet oder Animationen für die angegebene Gruppe nicht gestartet wurde wurde und das interne Storyboard NULL ist.

### <a name="remarks"></a>Hinweise

Nastavena ein Handler aufruft (aktiviert) Windows Animations-API OnStoryboardStatusChanges und OnStoryboardUpdated virtuelle Methoden. Ein Handler muss festgelegt werden, nachdem für die Gruppe angegebene Animation CAnimationController:: Animate aufgerufen wurde, da gekapseltes IUIAnimationStoryboard-Objekt erstellt.

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

Sucht nach einer Animationsgruppe, indem Sie seine Gruppen-ID.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt eine Gruppen-ID an.

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die Animationsgruppe oder NULL, wenn die Gruppe mit der angegebenen ID nicht gefunden wird.

### <a name="remarks"></a>Hinweise

Verwenden Sie diese Methode, um eine Animation aus zur Laufzeit zu suchen. Eine Gruppe erstellt und der internen Liste von Animationsgruppen hinzugefügt wird, wenn ein erstes Animationsobjekt mit einer bestimmten GroupID Animationscontroller hinzugefügt wird.

##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject

Sucht, die eine Variable angegebene Animation "Animation"-Objekts an.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parameter

*pVariable*<br/>
Ein Zeiger auf eine Animationsvariable.

*ppObject*<br/>
Die Ausgabe. Enthält einen Zeiger auf "Animation"-Objekts oder NULL.

*ppGroup*<br/>
Die Ausgabe. Enthält einen Zeiger zur Animationsgruppe, die die "Animation"-Objekts oder NULL enthält.

### <a name="return-value"></a>Rückgabewert

True, wenn das Objekt gefunden wurde. andernfalls "false".

### <a name="remarks"></a>Hinweise

Wird von Ereignishandlern aufgerufen, wenn dies erforderlich ist, ein Animationsobjekt von eingehenden Animationsvariablen gefunden.

##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart

Ein Keyframe, der Anfang des Storyboards darstellt.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart

Gibt einen Keyframe, der Anfang des Storyboards identifiziert.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Basiskeyframe, der den Anfang des Storyboards identifiziert.

### <a name="remarks"></a>Hinweise

Rufen Sie diesen Keyframe um andere Keyframes oder Übergänge den Zeitpunkt als Grundlage für den Beginn ein Storyboards.

##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager

Bietet Zugriff auf gekapselte IUIAnimationManager-Objekt.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf IUIAnimationManager-Schnittstelle oder NULL, wenn Fehler bei der Erstellung der Animations-Manager.

### <a name="remarks"></a>Hinweise

Wenn das aktuelle Betriebssystem Windows Animations-API nicht unterstützt, wird diese Methode gibt NULL zurück, und anschließend alle nachfolgenden Aufrufe von CAnimationController::IsValid gibt "false". Sie müssen möglicherweise IUIAnimationManager zugreifen kann, um die Schnittstellenmethoden aufrufen, die nicht von Animationscontroller umschlossen werden.

##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer

Bietet Zugriff auf gekapselte IUIAnimationTimer-Objekt.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf IUIAnimationTimer-Schnittstelle oder NULL, wenn Fehler bei der Erstellung des Animationszeitgebers für.

### <a name="remarks"></a>Hinweise

Wenn das aktuelle Betriebssystem Windows Animations-API nicht unterstützt, wird diese Methode gibt NULL zurück, und anschließend alle nachfolgenden Aufrufe von CAnimationController::IsValid gibt "false".

##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory

Ein Zeiger auf IUIAnimationTransitionFactory-Schnittstelle oder NULL, wenn Fehler bei der Erstellung der Übergangsbibliothek.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf IUIAnimationTransitionFactory oder NULL, wenn Fehler bei der Erstellung des Übergangsfactory.

### <a name="remarks"></a>Hinweise

Wenn das aktuelle Betriebssystem Windows Animations-API nicht unterstützt, wird diese Methode gibt NULL zurück, und anschließend alle nachfolgenden Aufrufe von CAnimationController::IsValid gibt "false".

##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary

Bietet Zugriff auf gekapselte IUIAnimationTransitionLibrary-Objekt.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf IUIAnimationTransitionLibrary-Schnittstelle oder NULL, wenn Fehler bei der Erstellung der Übergangsbibliothek.

### <a name="remarks"></a>Hinweise

Wenn das aktuelle Betriebssystem Windows Animations-API nicht unterstützt, wird diese Methode gibt NULL zurück, und anschließend alle nachfolgenden Aufrufe von CAnimationController::IsValid gibt "false".

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

Erfahren Sie, ob mindestens eine Gruppe Animation wiedergegeben wird.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Rückgabewert

True, wenn es eine Animation für diesen Animationscontroller ausgeführt. andernfalls "false".

### <a name="remarks"></a>Hinweise

Status der Animations-Manager überprüft, und gibt TRUE zurück, wenn der Status UI_ANIMATION_MANAGER_BUSY ist.

##  <a name="isvalid"></a>  CAnimationController::IsValid

Erfahren Sie, ob Animationscontroller gültig ist.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

True, wenn Animationscontroller gültig ist. andernfalls "false".

### <a name="remarks"></a>Hinweise

Diese Methode gibt "false" nur dann, wenn Windows Animations-API nicht unterstützt wird, auf das aktuelle Betriebssystem und die Erstellung der Animations-Manager ist fehlgeschlagen, da es nicht registriert ist. Sie müssen GetUIAnimationManager mindestens einmal nach der Initialisierung der COM-Bibliotheken, die dazu führen, dass bei der Einstellung dieses Flags aufrufen.

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

Gibt an, ob als Animationscontroller gültig oder nicht ist. Dieser Member ist auf "false" festgelegt, wenn das aktuelle Betriebssystem Windows Animations-API nicht unterstützt.

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups

Eine Liste der Animationsgruppen, die an diesen Animationscontroller gehören.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

Speichert einen Zeiger auf Animations-Manager-COM-Objekt.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

Speichert einen Zeiger auf Animation Timer COM-Objekt.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

Ein Zeiger auf ein verknüpftes CWnd-Objekt, das automatisch neu gezeichnet werden kann, wenn der Status der Animations-Manager geändert wurde oder Ereignis nach dem Update aufgetreten. NULL kann sein.

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

Speichert einen Zeiger auf Übergang Factory COM-Objekt.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

Speichert einen Zeiger auf Übergang Bibliothek COM-Objekt.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule

Vom Framework aufgerufen, wenn eine Animation für die angegebene Gruppe lediglich geplant wurde.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*pGroup*<br/>
Ein Zeiger auf eine Animationsgruppe, die geplant wurde.

### <a name="remarks"></a>Hinweise

Die Standardimplementierung Keyframes aus der angegebenen Gruppe entfernt, und wechselt von der Animationsvariablen, die der angegebenen Gruppe gehören. Kann in einer abgeleiteten Klasse zusätzliche Aktionen ausführen nach Animationszeitplan überschrieben werden.

##  <a name="onanimationintegervaluechanged"></a>  CAnimationController:: OnAnimationIntegerValueChanged

Wird von Framework aufgerufen, wenn es sich bei ganzzahligen Wert der Animationsvariablen geändert hat.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Parameter

*pGroup*<br/>
Ein Zeiger auf eine Animationsgruppe, die ein Animationsobjekt, dessen Wert enthält geändert hat.

*pObject*<br/>
Ein Zeiger auf eine Animationsobjekt, das eine Animationsvariable enthält, deren Wert geändert wurde.

*variable*<br/>
Ein Zeiger auf eine Animationsvariable.

*newValue*<br/>
Gibt die neuen Wert.

*prevValue*<br/>
Gibt die vorherige Wert an.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Variable Animationsereignisse mit EnableIntegerValueChangedEvent Namens für eine spezifische Animation-Variable oder ein Animationsobjekt aktiviert. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged

Wird aufgerufen, durch das Framework als Reaktion auf StatusChanged-Ereignis von der Animations-Manager.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parameter

*newStatus*<br/>
Neue Animation-Manager-Status.

*previousStatus*<br/>
Status des vorherigen Animation-Manager.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Animation-Manager-Ereignisse mit EnableAnimationManagerEvent aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Die Standardimplementierung aktualisiert ein verknüpftes Fensters, wenn er mit SetRelatedWnd festgelegt wurde.

##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate

Vom Framework aufgerufen, nachdem ein Animationsupdate abgeschlossen ist.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Timer-Ereignishandler mit EnableAnimationTimerEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate

Wird vom Framework aufgerufen, bevor ein Animationsupdate beginnt.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Timer-Ereignishandler mit EnableAnimationTimerEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow

Vom Framework aufgerufen, wenn eine minimale wünschenswert Framerate die Rendering-Framerate für eine Animation unterschreitet.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parameter

*fps*<br/>
Die aktuelle Framerate in Frames pro Sekunde.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Timer-Ereignishandler mit EnableAnimationTimerEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Die minimale wünschenswert Framerate wird durch SetFrameRateThreshold angegeben.

##  <a name="onanimationvaluechanged"></a>  CAnimationController:: OnAnimationValueChanged

Vom Framework aufgerufen, wenn der Wert der Animationsvariablen geändert hat.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Parameter

*pGroup*<br/>
Ein Zeiger auf eine Animationsgruppe, die ein Animationsobjekt, dessen Wert enthält geändert hat.

*pObject*<br/>
Ein Zeiger auf eine Animationsobjekt, das eine Animationsvariable enthält, deren Wert geändert wurde.

*variable*<br/>
Ein Zeiger auf eine Animationsvariable.

*newValue*<br/>
Gibt die neuen Wert.

*prevValue*<br/>
Gibt die vorherige Wert an.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Variable Animationsereignisse mit EnableValueChangedEvent Namens für eine spezifische Animation-Variable oder ein Animationsobjekt aktiviert. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

Vom Framework aufgerufen, rechts, bevor die Animation geplant wird.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*pGroup*<br/>
Ein Zeiger auf eine Animationsgruppe, deren Animation wird gestartet.

### <a name="remarks"></a>Hinweise

Dieser Aufruf wird an den zugehörigen CWnd weitergeleitet und kann in einer abgeleiteten Klasse zusätzlichen Aktionen ausführen, vor dem Start der Animation für die angegebene Gruppe überschrieben werden.

##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNew*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_CANCEL angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Lesen Windows Animations-API-Dokumentation für Weitere Informationen zu [Konfliktmanagement](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNew*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_TRIM angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Lesen Windows Animations-API-Dokumentation für Weitere Informationen zu [Konfliktmanagement](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNew*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_CONCLUDE angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Lesen Windows Animations-API-Dokumentation für Weitere Informationen zu [Konfliktmanagement](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNew*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_TRIM angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Lesen Windows Animations-API-Dokumentation für Weitere Informationen zu [Konfliktmanagement](/windows/desktop/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority).

##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged

Vom Framework aufgerufen, wenn die Storyboardstatus geändert hat.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parameter

*pGroup*<br/>
Ein Zeiger auf eine Animationsgruppe, die das Storyboard, dessen Status besitzt geändert hat.

*newStatus*<br/>
Gibt den neuen Status an.

*previousStatus*<br/>
Gibt den vorherigen Status.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Storyboardereignisse, die mit CAnimationController:: EnableStoryboardEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated

Vom Framework aufgerufen, wenn ein Storyboard aktualisiert wurde.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*pGroup*<br/>
Ein Zeiger auf eine Gruppe, die das Storyboard besitzt.

### <a name="remarks"></a>Hinweise

Diese Methode wird aufgerufen, wenn Sie die Storyboardereignisse, die mit CAnimationController:: EnableStoryboardEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

Entfernt alle Animationsgruppen aus Animationscontroller.

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Hinweise

Alle Gruppen werden gelöscht, deren Zeiger ist, wenn auf der Anwendungsebene gespeichert muss ungültig gemacht werden. Wenn CAnimationGroup:: M_bautodestroyanimationobjects für eine Gruppe gelöscht wird "true" ist, werden alle Animationsobjekte, die zu dieser Gruppe gehören gelöscht. Klicken Sie andernfalls ihre Verweise auf übergeordnete Animationscontroller werden auf NULL festgelegt werden, und sie an einen anderen Controller hinzugefügt werden können.

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

Entfernt eine Animationsgruppe mit der angegebenen ID aus Animationscontroller an.

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt an, Animation-Gruppen-ID.

### <a name="remarks"></a>Hinweise

Diese Methode wird eine Animationsgruppe aus der internen Liste von Gruppen entfernt und gelöscht, daher, wenn Sie einen Zeiger auf diese Animationsgruppe gespeichert haben, es muss ungültig gemacht werden. Wenn CAnimationGroup:: M_bautodestroyanimationobjects TRUE ist, werden alle Animationsobjekte, die zu dieser Gruppe gehören gelöscht. Klicken Sie andernfalls ihre Verweise auf übergeordnete Animationscontroller werden auf NULL festgelegt werden, und sie an einen anderen Controller hinzugefügt werden können.

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

Entfernen Sie ein Animationsobjekt aus Animationscontroller an.

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parameter

*pObject*<br/>
Ein Zeiger auf ein Animationsobjekt.

*bNoDelete*<br/>
Wenn dieser Parameter "true" wird das Objekt nach dem Entfernen nicht gelöscht werden.

### <a name="remarks"></a>Hinweise

Entfernt ein Animationsobjekt aus Animationscontroller und Animationsgruppe. Rufen Sie diese Funktion, wenn ein bestimmtes Objekt nicht mehr animiert werden soll, oder wenn Sie das Objekt in einer anderen Animationscontroller verschieben möchten. In den letzten muss die Groß-/Kleinschreibung bNoDelete "true" sein.

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

Entfernt Übergänge von Animationsobjekten, die der angegebenen Gruppe gehören.

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID.

### <a name="remarks"></a>Hinweise

Die Gruppe durchläuft die Animationobjekte und ClearTransitions(FALSE) für jede "Animation"-Objekts aufruft. Diese Methode wird vom Framework aufgerufen, nachdem die Animation geplant wurde.

##  <a name="schedulegroup"></a>  CAnimationController:: ScheduleGroup auf

Plant eine Animation.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Animation so planen Sie die Gruppen-ID an.

*time*<br/>
Gibt die Zeit zu planen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Animation wurde erfolgreich geplant wurde. FALSE, wenn das Storyboard wurde nicht erstellt werden soll, oder anderer Fehler auftritt.

### <a name="remarks"></a>Hinweise

Sie müssen AnimateGroup mit Parameter-bScheduleNow legen Sie auf "false" Vorherige ScheduleGroup aufrufen. Sie können angeben, auf die gewünschte Animation Zeit aus IUIAnimationTimer:: GetTime erhaltene abgerufen. Wenn es sich bei der Zeitparameter 0,0 festgelegt ist, wird die Animation für die aktuelle Uhrzeit geplant.

##  <a name="setrelatedwnd"></a>  CAnimationController:: SetRelatedWnd

Legt eine Beziehung zwischen den Animationscontroller und ein Fenster.

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf Window-Objekt festlegen.

### <a name="remarks"></a>Hinweise

Wenn ein verknüpftes CWnd-Objekt festgelegt ist, der Animationscontroller kann es automatisch aktualisieren (WM_PAINT-Meldung gesendet) Wenn der Status der Animations-Manager wurde geändert oder Ereignis Timer nach dem Update aufgetreten ist.

##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager

Leitet die Animations-Manager zum Aktualisieren der Werte aller Variablen der Animation an.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Hinweise

Aufrufen, die diese Methode der Animations-Manager auf aktuelle Zeit verschiebt, Status des Storyboards nach Bedarf ändern und aktualisieren alle Animationsvariablen, die an entsprechende interpolierte Werte. Diese Methode ruft intern timeNow und IUIAnimationManager. Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um dieses Verhalten zu ändern.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)
