---
title: Erstellen eines neuen C++ Projekts unter Linux in Visual Studio
ms.date: 06/11/2019
ms.assetid: 5d7c1d67-bc31-4f96-8622-2b4cf91372fd
ms.openlocfilehash: 0377e21177b29d998fc3e66bb1863dbc127c1fbe
ms.sourcegitcommit: fde637f823494532314790602c2819f889706ff6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67042709"
---
# <a name="create-a-new-linux-project"></a>Erstellen eines neuen Linux-Projekts

::: moniker range="vs-2015"

Linux-Projekte sind in Visual Studio 2017 und höher verfügbar.

::: moniker-end

Stellen Sie zunächst sicher, dass Sie die **Workload „Linux-Entwicklung“** für Visual Studio installiert haben. Weitere Informationen finden Sie unter [Herunterladen, Installieren und Einrichten der Linux-Workload](download-install-and-setup-the-linux-development-workload.md).

Wenn Sie ein neues C++-Projekt für Linux in Visual Studio erstellen, können Sie zwischen einem Visual Studio- und einem CMake-Projekt wählen. In diesem Artikel wird beschrieben, wie Sie ein Visual Studio-Projekt erstellen können. Informationen zum Arbeiten mit und Erstellen von CMake-Projekten finden Sie unter [Erstellen und Konfigurieren eines Linux CMake-Projekts](cmake-linux-project.md).

## <a name="to-create-a-new-linux-project"></a>So erstellen Sie ein neues Linux-Projekts

Führen Sie folgende Schritte aus, um ein neues Linux-Projekt in Visual Studio zu erstellen:

::: moniker range="vs-2019"

1. Wählen Sie in Visual Studio **Datei > Neues Projekt** aus, oder drücken Sie **STRG + UMSCHALT + N**.
1. Legen Sie die **Sprache** auf **C++** fest, und suchen Sie nach „Linux“. Wählen Sie den zu erstellenden Projekttyp aus, und klicken Sie dann auf **Weiter**. Geben Sie einen **Namen** und einen **Speicherort** an, und klicken Sie auf **Erstellen**.

   ![Neues Linux-Projekt](media/newproject-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

1. Wählen Sie in Visual Studio **Datei > Neues Projekt** aus, oder drücken Sie **STRG + UMSCHALT + N**.
1. Wählen Sie **Visual C++ > Plattformübergreifend > Linux** und anschließend den Projekttyp aus, den Sie erstellen möchten. Geben Sie einen **Namen** und einen **Speicherort** an, und klicken Sie dann auf **OK**.

   ![Neues Linux-Projekt](media/newproject.png)

::: moniker-end

   | Projekttyp | BESCHREIBUNG |
   | ------------ | --- |
   | **Blink (Raspberry)**           | Projekt für ein Raspberry Pi-Gerät mit Beispielcode für das Aufblinken einer LED |
   | **Konsolenanwendung (Linux)** | Projekt für alle Linux-Computer mit Beispielcode für die Ausgabe von Text an die Konsole |
   | **Leeres Projekt (Linux)**       | Projekt für alle Linux-Computer ohne Beispielcode |
   | **Makefile-Projekt (Linux)**    | Projekt für alle Linux-Computer, die mithilfe eines Standard-Makefile-Buildsystems erstellt wurden |

   ::: moniker range="vs-2019"

   Visual Studio 2019 ermöglicht Ihnen die Erstellung ein neues CMake-Projekts. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren eines Linux CMake-Projekts](cmake-linux-project.md).
   
   ::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren eines Linux-Projekts](configure-a-linux-project.md)
