---
title: Debuggen im gemischten Modus wird nur unterstützt, wenn Microsoft .NET Framework 2,0 oder 3,0 verwendet wird | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b20ef6b81e4d7162fd230d9d0c3437fe1b5232c1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730919"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Debuggen im gemischten Modus wird nur bei Verwendung von Microsoft .NET Framework, Version 2.0 oder 3.0, unterstützt
Ältere Versionen von Microsoft .NET Framework 2.0 bieten keine Unterstützung für das Debuggen im gemischten Modus von 64-Bit-Prozessen. Dies bedeutet, dass Sie während des Debuggens nicht von verwaltetem Code zu systemeigenem Code oder von systemeigenem Code zu verwaltetem Code wechseln können.

 Sie können Folgendes tun, um dieses Problem zu umgehen:

- Aktualisieren Sie das Projekt, um Microsoft .NET Framework 2.0 oder 3.0 zu verwenden.

- Debuggen Sie den verwalteten und den systemeigenen Code in separaten Debugsitzungen.

- Debuggen Sie den gemischten Code als 32-Bit-Prozess, wie in den folgenden Prozeduren beschrieben.

### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>So ändern Sie das Betriebssystem in 32-Bit (Visual Basic oder C#)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie im Kontextmenü auf **Eigenschaften**.

2. Klicken Sie auf den Eigenschaftenseiten auf die Registerkarte **Kompilieren** oder auf die Registerkarte **Debuggen**.

3. Klicken Sie auf **Plattform**, und wählen Sie **x86** aus der Liste der Plattformen aus.

     Die Visual Basic- und C#-Compiler erzeugen standardmäßig Code, der mit jeder CPU ausgeführt werden kann. Auf einem 64-Bit-Computer werden diese Binärdateien als 64-Bit-Prozesse ausgeführt. Wählen Sie **Win32** anstelle von **AnyCPU** aus, wenn Sie die Ausführung in einem 32-Bit-Prozess wünschen.

### <a name="to-change-the-operating-system-to-32-bit-cc"></a>So ändern Sie das Betriebssystem in 32-Bit (C/C++)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie im Kontextmenü auf **Eigenschaften**.

     Klicken Sie auf den Eigenschaftenseiten auf **Plattform**, und wählen Sie **Win32** aus der Liste der Plattformen aus.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Siehe [Einrichten des SQL-Debuggens](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Siehe auch
- [Debuggen von 64-Bit-Anwendungen](../debugger/debug-64-bit-applications.md)