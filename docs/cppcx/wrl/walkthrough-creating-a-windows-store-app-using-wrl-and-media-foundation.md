---
title: 'Exemplarische Vorgehensweise: Erstellen einer UWP-app mithilfe von WRL und Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 1eee353bb13a3fa03fda42c3d0f7a4103dc5ad13
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450143"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Exemplarische Vorgehensweise: Erstellen einer UWP-app mithilfe von WRL und Media Foundation

> [!NOTE]
> Für neue UWP-apps und Komponenten, empfehlen wir die Verwendung von [C++ / WinRT](/windows/uwp/cpp-and-winrt-apis/), einen neuen C ++ 17-standardsprachprojektion für Windows-Runtime-APIs. C++ / WinRT finden Sie in das Windows 10 SDK Version 1803 gerechnet. C++ / WinRT ist nur in Headerdateien implementiert wird, und soll Sie mit erstklassigen Zugriff auf die moderne Windows-API bereitstellen.

In diesem Tutorial erfahren Sie, wie zur Verwendung der Windows-Runtime C++ Template Library (WRL), um eine app für die universelle Windows-Plattform (UWP) erstellen, verwendet [Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk).

In diesem Beispiel wird eine benutzerdefinierte Media Foundation-Transformation erstellt, in der ein Graustufeneffekt auf Bilder angewendet wird, die über eine Webcam erfasst werden. Die App verwendet C++ zum Definieren der benutzerdefinierten Transformation und C# zum Verwenden der Komponente für das Transformieren der erfassten Bilder.

> [!NOTE]
> Anstelle von C# können Sie auch JavaScript, Visual Basic oder C++ verwenden, um die benutzerdefinierte Transformierenkomponente zu verwenden.

In den meisten Fällen können Sie mithilfe C++ / CX verwenden, um die Windows-Runtime zu erstellen. Allerdings müssen gelegentlich Sie die WRL verwenden. Wenn Sie eine medienerweiterung für Microsoft Media Foundation erstellen, müssen Sie z. B. eine Komponente erstellen, die sowohl COM-als auch Windows-Runtime-Schnittstellen implementiert. Da C++ / CX kann nur Windows-Runtime-Objekte erstellen, Sie müssen zum Erstellen einer medienerweiterung die WRL verwenden, da es sich um die Implementierung von sowohl COM-als auch Windows-Runtime-Schnittstellen ermöglicht.

> [!NOTE]
> Auch wenn dieses Codebeispiel lang ist, stellt es das erforderliche Minimum dar, um eine nützliche Media Foundation-Transformation zu erstellen. Sie können es als Ausgangspunkt für Ihre eigene benutzerdefinierte Transformation verwenden. In diesem Beispiel basiert auf der [medienerweiterungen](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096), anzuwendende medienerweiterungen verwendet Effekte auf Videos, decodieren, und schemahandler zu erstellen, die Medienstreams generieren.

## <a name="prerequisites"></a>Vorraussetzungen

- In Visual Studio 2017 und höher ist die UWP-Unterstützung eine optionale Komponente. Um es zu installieren, öffnen Sie Visual Studio-Installer über das Windows-Startmenü aus, und suchen Sie Ihre Version von Visual Studio. Wählen Sie **ändern** und stellen Sie sicher, dass die **Entwicklung von universellen Windows-Plattform** Kachel aktiviert ist. Klicken Sie unter **optionale Komponenten** überprüfen  **C++ -Tools für UWP (v141)** für Visual Studio 2017 oder  **C++ -Tools für UWP (v142)** für Visual Studio-2019. Überprüfen Sie die Version des Windows SDK, das Sie verwenden möchten. 

- Erleben Sie mit der [Windows-Runtime](https://msdn.microsoft.com/library/windows/apps/br211377.aspx).

- Erfahrungen mit COM.

- Eine Webcam.

## <a name="key-points"></a>Wesentliche Punkte

- Verwenden Sie zum Erstellen einer benutzerdefinierten Media Foundation-Komponente eine MIDL-Definitionsdatei (Microsoft Interface Definition Language) zum Definieren einer Schnittstelle, Implementieren dieser Schnittstelle und zum Einstellen derselben, dass sie aus anderen Komponenten aktiviert werden kann.

- Die `namespace` und `runtimeclass` Attribute, und die `NTDDI_WIN8` [Version](/windows/desktop/Midl/version) Attributwert sind wichtige Bestandteile der MIDL-Definition für eine Media Foundation-Komponente, die WRL verwendet.

- [Microsoft::wrl::RuntimeClass](runtimeclass-class.md) ist die Basisklasse für die benutzerdefinierte Media Foundation-Komponente. Die [winrtclassiccommix](runtimeclasstype-enumeration.md) Enum-Wert, der als Vorlagenargument angegeben wird, markiert die Klasse für die Verwendung sowohl als eine Windows-Runtime-Klasse einer klassischen COM-Runtime-Klasse.

- Die [InspectableClass](inspectableclass-macro.md) -Makro implementiert grundlegende COM-Funktionen wie die verweiszählung und die `QueryInterface` -Methode und legt die Laufzeit Klassennamen und die-Vertrauensstufe.

- Verwenden Sie die Microsoft:: wrl::[Modulklasse](module-class.md) um DLL-Einstiegspunkt-Funktionen zu implementieren, wie z. B. ["dllgetactivationfactory"](https://msdn.microsoft.com/library/br205771.aspx), ["DllCanUnloadNow"](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow), und [ DllGetClassObject](/windows/desktop/api/combaseapi/nf-combaseapi-dllgetclassobject).

- Verknüpfen Sie die Komponenten-DLL mit „runtimeobject.lib“. Geben Sie auch [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) der Linkerzeile an, um Windows-Metadaten zu generieren.

- Verwenden Sie Projektverweise, auf die WRL-Komponenten für UWP-apps zugänglich zu machen.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Verwendung die WRL auf der Graustufe Media Foundation erstellen Transformationskomponente

1. Erstellen Sie in Visual Studio eine **leere Projektmappe** Projekt. Nennen Sie das Projekt, z. B. *MediaCapture*.

1. Hinzufügen einer **DLL (Universal Windows)** Projekt der Projektmappe. Nennen Sie das Projekt, z. B. *GrayscaleTransform*.

1. Hinzufügen einer **Midl-Datei (.idl)** Datei zum Projekt. Nennen Sie die Datei, z. B. *"grayscaletransform.idl"* .

1. "Grayscaletransform.idl" diesen Code hinzufügen:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Verwenden Sie den folgenden Code ersetzen Sie den Inhalt der `pch.h`:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Fügen Sie auf das Projekt eine neue Headerdatei hinzu, nennen Sie es `BufferLock.h`, und Ersetzen Sie den Inhalt durch den folgenden Code:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h` in diesem Beispiel wird nicht verwendet werden. Sie können ihn bei Bedarf aus dem Projekt entfernen.

1. Verwenden Sie den folgenden Code ersetzen Sie den Inhalt der `GrayscaleTransform.cpp`:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Fügen Sie eine neue Moduldefinitionsdatei-Datei zum Projekt, nennen Sie es `GrayscaleTransform.def`, und fügen Sie folgenden Code:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Verwenden Sie den folgenden Code ersetzen Sie den Inhalt der `dllmain.cpp`:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. Des Projekts **Eigenschaftenseiten** Dialogfeld Feld, legen Sie den folgenden **Linker** Eigenschaften.

   1. Klicken Sie unter **Eingabe**, für die **Moduldefinitionsdatei**, geben Sie `GrayScaleTransform.def`.

   1. Außerdem **Eingabe**, hinzufügen `runtimeobject.lib`, `mfuuid.lib`, und `mfplat.lib` auf die **zusätzliche Abhängigkeiten** Eigenschaft.

   1. Klicken Sie unter **Windows-Metadaten**legen **Windows-Metadaten generieren** zu **Ja (/ WINMD)** .

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Die WRL der benutzerdefinierten Media Foundation-Komponente aus einer c#-app verwenden.

1. Fügen Sie einen neuen **c# leere App (Universelles Windows)** Projekt die `MediaCapture` Lösung. Nennen Sie das Projekt, z. B. *MediaCapture*.

1. In der **MediaCapture** fügen einen Verweis auf die `GrayscaleTransform` Projekt. Informationen dazu finden Sie unter [Vorgehensweise: Hinzufügen und Entfernen von Verweisen mit dem Verweis-Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. In `Package.appxmanifest`auf die **Funktionen** Registerkarte **Mikrofon** und **Webcam**. Beide Funktionen sind erforderlich, um Fotos von der Webcam zu erfassen.

1. In `MainPage.xaml`, fügen Sie diesen Code in das Stammverzeichnis [Raster](https://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.grid.aspx) Element:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Verwenden Sie den folgenden Code ersetzen Sie den Inhalt der `MainPage.xaml.cs`:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

Die folgende Abbildung zeigt die `MediaCapture app`.

![MediaCapture-app zeichnet ein Foto](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Nächste Schritte

Im Beispiel wird gezeigt, wie Fotos von der standardmäßigen Webcam nacheinander erfasst werden. Die [medienerweiterungen](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) finden Sie weitere. Es veranschaulicht die Aufzählung von Webcamgeräten und die Arbeit mit lokalen Schemahandlern, und es veranschaulicht zusätzliche Medieneffekte, die bei einzelnen Fotos und Videostreams funktionieren.

## <a name="see-also"></a>Siehe auch

[C++-Vorlagenbibliothek für Windows-Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/desktop/medfound/microsoft-media-foundation-sdk)<br/>
[Beispiel für die medienerweiterungen](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
