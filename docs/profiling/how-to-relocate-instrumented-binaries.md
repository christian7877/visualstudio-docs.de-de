---
title: 'Vorgehensweise: Verschieben instrumentierter Binärdateien | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cddbb0b3e27b841441937b7256ea32d722e25f5e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2019
ms.locfileid: "74774899"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Vorgehensweise: Verschieben instrumentierter Binärdateien

Während der Instrumentation werden Sonden in die Binärdatei eingeführt, um die Anwendungsleistung zu messen. Wenn Sie sich entscheiden, die instrumentierte Binärdatei an einem anderen Ort zu speichern, wird eine Kopie der ursprünglichen Binärdatei instrumentiert und am entsprechenden Speicherort abgelegt. Diese Option ist nützlich, wenn Sie vermeiden möchten, dass der Profiler Ihre ursprüngliche Binärdatei umbenennt. Wenn die Binärdatei nicht an einen anderen Speicherort ausgelagert wird, wird die ursprüngliche Version der Binärdatei überschrieben.

## <a name="to-relocate-instrumented-binary"></a>Verschieben von gemessenen Binärdateien

1. Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf den **Eigenschaftenseiten**auf die Eigenschaften von **Binärdateien** .

3. Aktivieren Sie das Kontrollkästchen **Gemessene Binärdateien verschieben** .

4. Geben Sie den Speicherort für die instrumentierte Binärdatei an.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)
[VSInstr](../profiling/vsinstr.md)
