---
title: Anwenden von Bearbeitungen im Umbruch Modus mit "Bearbeiten und Fortfahren" | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05340b4922262eb134aca8fef4bf215342e5a997
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734033"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Vorgehensweise: Anwenden von Bearbeitungen im Break-Modus mit "Bearbeiten und Fortfahren" (Visual Basic)
Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.

Informationen zu Einschränkungen bei der Verwendung von bearbeiten und Fortfahren beim Debuggen finden Sie [unter Unterstützte Code Änderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus

1. Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:

    - Legen Sie einen Breakpoint im Code fest, wählen Sie im Menü **Debuggen** den Befehl **Debuggen starten** aus, und warten Sie, bis die Anwendung den Breakpoint erreicht.

         - oder -

    - Beginnen Sie mit dem Debuggen, und wählen Sie anschließend im Menü **Debuggen** den Befehl **Alle unterbrechen** aus.

         - oder -

    - Wenn eine Ausnahme auftritt, wählen Sie im Ausnahmen- **Assistenten**die Option **Bearbeitung aktivieren** aus.

2. Nehmen Sie die gewünschten und unterstützten Codeänderungen vor.

     Weitere Informationen finden Sie [unter Unterstützte Code ÄnderungenC# (und Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.

3. Klicken Sie im Menü **Debuggen** auf **Weiter**, um mit der Ausführung fortzufahren.

     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.

## <a name="see-also"></a>Siehe auch
- [Unterstützte Code ÄnderungenC# (und Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
