---
title: Scrollleisten-Zuordnungsmodus und -Leistenmodus
ms.date: 09/25/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22436c221813ec4c3701d208fc74a96b403fff9c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591397"
---
# <a name="how-to-customize-the-scroll-bar"></a>Vorgehensweise: Anpassen der Scrollleiste

Wenn Sie mit umfangreichen Codedateien arbeiten, kann es schwierig sein, den Überblick zu behalten, wo sich die einzelnen Elemente in der Datei befinden. Sie können die Scrollleiste des Code-Editors anpassen, um sich ein Gesamtbild davon zu machen, was in Ihrem Code geschieht.

## <a name="annotations"></a>Anmerkungen

Sie können auswählen, ob die Scrollleiste Anmerkungen wie Codeänderungen, Haltepunkte, Lesezeichen, Fehler und die Position der Einfügemarke anzeigt.

   1. Öffnen Sie die Optionsseite **Scrollleisten**, indem Sie **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **Scrollleisten** auswählen.

   2. Wählen Sie **Anmerkungen über vertikaler Bildlaufleiste anzeigen** aus, und klicken Sie dann auf die Anmerkungen, die angezeigt werden sollen. Die verfügbaren Anmerkungen sind:

      - Änderungen
      - Markierungen
      - Fehler
      - Position der Einfügemarke

      > [!TIP]
      > Die Option **Markierungen anzeigen** umfasst Haltepunkte und Lesezeichen.

Probieren Sie es aus, indem Sie eine umfangreiche Codedatei öffnen und Text ersetzen, der an mehreren Stellen in der Datei vorkommt. Die Bildlaufleiste zeigt die Auswirkungen der Ersetzungen an. Sie können also Änderungen rückgängig machen, wenn ein Element nicht ersetzt werden soll.

So sieht die Bildlaufleiste aus, nachdem eine Zeichenfolge gesucht wurde. Beachten Sie, dass alle Instanzen der Zeichenfolge in der Scrollleiste angezeigt werden.

![Visual Studio-Scrollleiste nach der Suche nach einer Zeichenfolge](../ide/media/enhancedscrollbarsearch.png)

So sieht die Bildlaufleiste aus, nachdem alle Instanzen der Zeichenfolge ersetzt wurden. Die roten Markierungen in die Scrollleiste zeigen an, wo durch die Textersetzung Fehler aufgetreten sind.

![Visual Studio-Scrollleiste mit Fehlern nach dem Ersetzen einer Zeichenfolge](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Anzeigemodi

Die Scrollleiste verfügt über zwei Modi: den Leistenmodus und den Zuordnungsmodus.

### <a name="bar-mode"></a>Leistenmodus

Im *Leistenmodus* werden Anmerkungsindikatoren auf der Scrollleiste angezeigt. Wenn Sie auf die Scrollleiste klicken, wird die Seite nach oben oder unten gescrollt, der Cursor springt aber nicht an die entsprechende Stelle in der Datei.

### <a name="map-mode"></a>Zuordnungsmodus

Wenn Sie im *Zuordnungsmodus* auf eine Position in der Scrollleiste klicken, springt der Cursor zu dieser Position in der Datei, anstatt nur eine Seite nach oben oder unten zu scrollen. Codezeilen werden als Miniaturbild auf der Scrollleiste angezeigt. Sie können auswählen, wie breit die Zuordnungsspalte ist, indem Sie einen Wert in **Quellübersicht** auswählen. Um eine größere Vorschau des Codes zu aktivieren, wenn Sie den Mauszeiger auf der Zuordnung positionieren, wählen Sie die Option **Vorschau-QuickInfo anzeigen** aus. Zugeklappte Bereiche werden anders schattiert und durch einen Doppelklick aufgeklappt.

> [!TIP]
> Sie können die Miniaturcodeansicht im Zuordnungsmodus deaktivieren, indem Sie **Quellübersicht** auf **Aus** festlegen. Wenn **Vorschau-QuickInfo anzeigen** ausgewählt ist, sehen Sie immer noch eine Vorschau des Codes an dieser Stelle, wenn Sie den Mauszeiger auf der Scrollleiste positionieren, und der Mauszeiger springt immer noch zu dieser Stelle in der Datei, wenn Sie klicken.

Die folgende Abbildung zeigt das Suchbeispiel, wenn der Zuordnungsmodus aktiviert und die Breite auf **Mittel** festgelegt ist:

![Visual Studio-Scrollleiste im Zuordnungsmodus](../ide/media/enhancedscrollbar.png)

Die folgende Abbildung zeigt die Option **Vorschau-QuickInfo anzeigen**:

![Visual Studio-Scrollleiste mit QuickInfo](../ide/media/enhancedscrollbarsearchtooltip.png)

## <a name="see-also"></a>Siehe auch

- [Features des Code-Editors](../ide/writing-code-in-the-code-and-text-editor.md)
