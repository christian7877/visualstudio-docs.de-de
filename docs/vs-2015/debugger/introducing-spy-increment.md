---
title: Einführung in Spy++ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35e9fa2d75528549f8c55f5b52dbd4c4aa2271a6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431458"
---
# <a name="introducing-spy"></a>Einführung in Spy++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit Spy++ können Sie die folgenden Aufgaben ausführen:  
  
- eine grafische Struktur von Beziehungen zwischen Systemobjekten anzeigen. Dazu gehören [Prozesse](../debugger/processes-view.md), [Threads](../debugger/threads-view.md)und [Fenster](../debugger/windows-view.md).  
  
- nach bestimmten [Fenstern](../debugger/how-to-search-for-a-window-in-windows-view.md), [Threads](../debugger/how-to-search-for-a-thread-in-threads-view.md), [Prozessen](../debugger/how-to-search-for-a-process-in-processes-view.md)oder [Nachrichten](../debugger/how-to-search-for-a-message-in-messages-view.md)suchen  
  
- die Eigenschaften von ausgewählten [Fenstern](../debugger/how-to-display-window-properties.md), [Threads](../debugger/how-to-display-thread-properties.md), [Prozessen](../debugger/how-to-display-process-properties.md)oder [Nachrichten](../debugger/how-to-display-message-properties.md)anzeigen  
  
- ein Fenster, einen Thread, Prozess oder eine Nachricht direkt in der Ansicht auswählen  
  
- das [Suchtool](../debugger/how-to-use-the-finder-tool.md) verwenden, um Fenster über die Positionierung des Mauszeigers auszuwählen  
  
- **Meldungsoptionen** über komplexe Auswahlparameter für die Nachrichtenprotokollierung festlegen  
  
  Spy++ verfügt über eine Symbolleiste und Hyperlinks, um Ihnen die Arbeit zu erleichtern. Darüber hinaus stellt es den Befehl **Aktualisieren** bereit, um die aktive Ansicht zu aktualisieren, ein **Tool zum Suchen von Fenstern** für leichteres Nachverfolgen und das Dialogfeld **Schriftart** zum Anpassen der Ansichtsfenster. Darüber hinaus können Sie mit Spy++ Benutzereinstellungen speichern und wiederherstellen.  
  
  Sie können in verschiedenen Spy++-Fenstern einen Rechtsklick ausführen, um ein Kontextmenü mit häufig verwendeten Befehlen anzuzeigen. Welche Befehle angezeigt werden, hängt davon ab, wo sich der Zeiger befindet. Wenn Sie zum Beispiel in der Fensteransicht mit der rechten Maustaste auf einen Eintrag klicken, das ausgewählte Fenster sichtbar ist und Sie anschließend im Kontextmenü auf **Hervorheben** klicken, blinkt der Rahmen des ausgewählten Fensters auf, sodass Sie es leichter finden können.  
  
> [!NOTE]
> Es gibt zwei weitere Hilfsprogramme, die Spy++ ähneln: PView, das Informationen über Prozesse und Threads und DDESPY anzeigt. EXE-Datei, Sie können die (DDE, Dynamic Data Exchange)-Nachrichten zu überwachen.  
  
## <a name="64-bit-operating-systems"></a>64-Bit-Betriebssysteme  
 Es gibt zwei Versionen von Spy++. Die erste Version namens Spy++ (spyxx.exe) dient zum Anzeigen von Nachrichten an ein Fenster, das in einem 32-Bit-Prozess ausgeführt wird. Visual Studio wird z.B. in einem 32-Bit-Prozess ausgeführt. Sie können Spy++ daher dazu verwenden, um Nachrichten an den **Projektmappen-Explorer**anzuzeigen. Da die Standardkonfiguration für die meisten Builds in Visual Studio in einem 32-Bit-Prozess ausgeführt wird, ist diese erste Version von Spy++ diejenige, die im Menü unter **Extras** in Visual Studio verfügbar ist.  
  
 Die zweite Version namens Spy++ (64-Bit) (spyxx_amd64.exe) dient zum Anzeigen von Nachrichten an ein Fenster, das in einem 64-Bit-Prozess ausgeführt wird. In einem 64-Bit-Betriebssystem wird z.B. Notepad in einem 64-Bit-Prozess ausgeführt. Sie können Spy++ (64-Bit) daher dazu verwenden, an Notepad gesendete Nachrichten anzuzeigen. Spy++ (64-Bit) befindet sich in der Regel in  
  
 ..\\*Visual Studio-Installationsordner*\Common7\Tools\spyxx_amd64.exe.  
  
 Sie können beide Versionen von Spy++ direkt über die Befehlszeile ausführen.  
  
> [!NOTE]
> Obwohl der Dateiname von Spy++ (64-Bit) „amd“ enthält, kann die Datei auf allen x64-Betriebssystemen von Windows aufgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von Spy++](../debugger/using-spy-increment.md)   
 [Spy++-Ansichten](../debugger/spy-increment-views.md)   
 [Spy++-Referenz](../debugger/spy-increment-reference.md)
