---
title: 'Fehler: das Debuggen von isn&#39;t ist möglich, da ein Kernel Debugger auf dem System aktiviert ist. Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a966869ff1d200a51c6019a6ae937bea7c447bd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737749"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Fehler: Debuggen&#39;von isn t möglich, da ein Kernel Debugger auf dem System aktiviert ist.
Beim Debuggen von verwaltetem Code kann die folgende Fehlermeldung ausgegeben werden:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Diese Meldung wird angezeigt, wenn Sie versuchen, verwalteten Code zu debuggen:

- auf einem [!INCLUDE[win7](../debugger/includes/win7_md.md)]- oder [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]-System, das im Debugmodus gestartet wurde.

- Die Anwendung verwendet die CLR-Version 2.0, 3.0 oder 3.5.

## <a name="solution"></a>Lösung

#### <a name="to-fix-this-problem"></a>So beheben Sie dieses Problem

- Aktualisieren Sie die Anwendung auf CLR-Version 4.0 oder 4.5.

   – oder –

- Deaktivieren Sie Kerneldebugging, und debuggen Sie in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   – oder –

- Debuggen Sie mit dem Kerneldebugger anstatt mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   – oder –

- Deaktivieren Sie im Kerneldebugger die Benutzermodusausnahmen.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>So deaktivieren Sie Kerneldebugging in der aktuellen Sitzung

- Geben Sie an der Eingabeaufforderung Folgendes ein:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>So deaktivieren Sie Kerneldebugging für alle Sitzungen (Windows Vista und Windows 7)

1. Geben Sie an der Eingabeaufforderung Folgendes ein:

    ```cmd
    bcdedit /debug off
    ```

2. Starten Sie den Computer neu.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>So deaktivieren Sie Kerneldebuggen für alle Sitzungen (andere Windows-Betriebssysteme)

1. Suchen Sie die Datei „boot.ini“ auf dem Systemlaufwerk (normalerweise C:\\). Die Datei "boot.ini" ist möglicherweise versteckt installiert und schreibgeschützt. Verwenden Sie zur Anzeige der Datei daher folgenden Befehl:

    ```cmd
    dir /ASH
    ```

2. Öffnen Sie "boot.ini" im Editor, und entfernen Sie die folgenden Optionen:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Starten Sie den Computer neu.

#### <a name="to-debug-with-the-kernel-debugger"></a>So debuggen Sie mit dem Kerneldebugger

1. Wenn der Kerneldebugger verknüpft ist, werden Sie in einer Meldung gefragt, ob Sie das Debuggen fortsetzen möchten. Klicken Sie auf die Schaltfläche, um den Vorgang fortzusetzen.

2. Sie erhalten möglicherweise einen `User break exception(Int 3).`-Wert. Geben Sie in diesem Fall den folgenden Befehl für den Kerneldebugger ein, um das Debuggen fortzusetzen:

     `gn`

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
