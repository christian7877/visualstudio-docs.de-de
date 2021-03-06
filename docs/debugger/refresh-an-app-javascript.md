---
title: Aktualisieren einer UWP-App | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 0b1d19c0b607d2c5a09fddc9d4550230e478d57a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730313"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Aktualisieren einer UWP-app in Visual Studio

 Sie können während des Debuggens Änderungen am Code vornehmen und dann eine UWP-App mithilfe von JavaScript aktualisieren, indem Sie auf der Symbolleiste **Debuggen** die Schaltfläche **Windows-APP aktualisieren** auswählen. Durch Auswählen dieser Schaltfläche wird die App erneut geladen, ohne den Debugger zu beenden und erneut zu starten. Die Aktualisierungsfunktion ermöglicht es Ihnen, HTML, CSS und JavaScript-Code zu ändern und das Ergebnis schnell anzuzeigen. Diese Funktion wird für UWP-Apps unterstützt.

 Aktualisieren hält weder den App-Zustand aufrecht noch reflektiert es die folgenden Änderungen zur App:

- Paketmanifestdateiänderungen, einschließlich Änderungen an den im Paketmanifest angegebenen Bildern.

- Verweisänderungen, wie das Hinzufügen oder Entfernen eines SDK-Verweises, oder Änderungen an den Komponenten für Windows-Runtime (.winmd-Dateien).

- Ressourcenänderungen, wie Änderungen an den Zeichenfolgen in .resjson-Dateien.

- Projektdateiänderungen, die zu Pfadnamenänderungen, neuen Projektdateien oder gelöschten Dateien führen.

- Projekt- und Elementeigenschaftenänderungen, wie Änderungen am ausgewählten Debugging-Gerät oder Änderungen an der Paketaktion für eine Datei (im Eigenschaftenfenster).

> [!IMPORTANT]
> Wenn Sie Verweise oder das Paketmanifest ändern oder andere Änderungen vornehmen, die in der vorangehenden Liste aufgeführt sind, müssen Sie den Debugger beenden und neu starten, um HTML-, CSS- und JavaScript-Quelldateien zu aktualisieren.

### <a name="to-refresh-an-app"></a>So aktualisieren Sie eine App

1. Wenn das UWP-Projekt in Visual Studio geöffnet ist, wählen Sie **lokaler Computer** als Debugziel aus.

     ![Liste der debugziele auswählen](../debugger/media/js_select_target.png "JS_Select_Target")

3. Drücken Sie F5, um die App im Debugmodus auszuführen.

4. Wechseln Sie zu Visual Studio.

5. Bearbeiten Sie auf der Startseite Ihrer UWP-App einige HTML-Code.

7. Klicken Sie auf die Schaltfläche **Windows-APP aktualisieren** , die wie folgt aussieht: ![Schaltfläche Windows-APP aktualisieren](../debugger/media/js_refresh.png "JS_Refresh"). (Oder drücken Sie F4)

8. Wechseln Sie zur App. Die APP wird erneut geladen, und der aktualisierte HTML-Code wird zum Rendering der APP verwendet.

## <a name="see-also"></a>Siehe auch
- [Schnellstart: Debuggen von HTML und CSS](../debugger/quickstart-debug-html-and-css.md)