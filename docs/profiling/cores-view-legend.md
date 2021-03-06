---
title: Legende der Kernansicht | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.legend
helpviewer_keywords:
- Concurrency Visualizer, Cores View Legend
ms.assetid: e160384c-fcfe-49b3-86b7-229adb736c51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ea3184fbcd3561b88521f7dbdf4bf44c925150d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553162"
---
# <a name="cores-view-legend"></a>Legende der Kernansicht
Die Legende der Kernansicht identifiziert jeden Thread durch Farbe und Namen. Sie enthält folgende Spalten: Anzahl der kernübergreifenden Kontextwechsel, Gesamtzahl der Kontextwechsel und Prozentsatz der Kontextwechsel, die durch Kerne verlaufen. Die Legende ist nach der Anzahl der kernübergreifenden Kontextwechsel in absteigender Reihenfolge angeordnet.

 Sie können in der Legende Zeilen auswählen, um Threads zu filtern, die auf der Zeitachse angezeigt werden. Nur die ausgewählten Threads werden auf der Zeitachse angezeigt. Wenn keine Zeilen ausgewählt sind, werden alle Zeilen auf der Zeitachse angezeigt.

 Kernübergreifende Kontextwechsel erfordern mehr Verwaltungsaufwand und sind leistungsintensiver als Wechsel, die auf dem logischen Kern verbleiben. Während der Kontextwechsel werden die Prozessorregister gespeichert und wiederhergestellt. Der Betriebssystem-Kernelcode wird ausgeführt, die Übersetzungslookaside-Puffereinträge werden neu geladen, und die Prozessorpipeline wird geleert. Kernübergreifende Kontextwechsel können sogar teurer als andere Kontextwechsel sein, da die Cachedaten für diesen Thread auf einem anderen Kern ungültig sind. Bei einem Thread hingegen, für den der Kontextwechsel auf dem Kern erfolgt, auf dem er zuvor ausgeführt wurde, sind die nützlichen Daten wahrscheinlich immer noch im Cache vorhanden. Die Anzahl kernübergreifender Kontextwechsel kann aufgrund von Versuchen, die Threadaffinität zu verwalten, zunehmen. Wenn die Leistung zudem beeinträchtigt ist, sollten Sie sich um eine Lösung bemühen. Beginnen Sie damit, die Threadaffinität zu beseitigen, und beobachten Sie, wie sich das kernübergreifende Verhalten daraufhin verändert.

 In der folgenden Tabelle werden die Legendenelemente beschrieben.

|Element|Definition|
|-------------|----------------|
|Thread Name|Zeigt die Farbe des Threads auf der Zeitachse der vorherigen Kerne sowie den Namen des Threads|
|Kernübergreifende Kontextwechsel|Die Anzahl der Kontextwechsel für einen Thread, der zudem von einem logischen Kern zu einem anderen umgeschaltet hat. Dabei wird nicht zwischen kernübergreifenden Kontextwechseln unterschieden, die von einem Prozessorwürfel zu einem anderen wechseln, und jenen, die auf dem gleichen Würfel bleiben.|
|Gesamte Kontextwechsel|Die Gesamtzahl der Kontextwechsel für einen angegebenen Thread während des Samplingzeitraums. Jede Kontextänderung eines Threads (z.B. von der Ausführung zur Synchronisierung) entspricht einem Kontextwechsel.|
|Prozentualer Anteil der Kontextwechsel, die durch Kerne verlaufen|Dieser Anteil wird als Prozentsatz ausgedrückt und entsteht dadurch, dass die Anzahl der kernübergreifenden Kontextwechsel durch die Gesamtzahl der Kontextwechsel dividiert wird. Je höher der Prozentsatz, desto stärker wirkt sich der Aufwand der kernübergreifenden Kontextwechsel auf die Leistung dieses speziellen Threads aus.|

## <a name="see-also"></a>Siehe auch
- [Kernansicht](../profiling/cores-view.md)