---
title: Registrierung und Auswahl (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3d6ca60c74ae9956f38418ea6048bb0c8050be2c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724509"
---
# <a name="registration-and-selection-source-control-vspackage"></a>Registrierung und Auswahl (Quellcodeverwaltungs-VSPackage)
Ein Quellcodeverwaltungs-VSPackage muss registriert werden, um es für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügbar zu machen. Wenn mehr als ein Quellcodeverwaltungs-VSPackage registriert ist, kann der Benutzer auswählen, welches VSPackage zu den entsprechenden Zeiten geladen werden soll. Weitere Informationen zu VSPackages und deren Registrierung finden Sie unter [VSPackages](../../extensibility/internals/vspackages.md) .

## <a name="registering-a-source-control-package"></a>Registrieren eines Quell Code Verwaltungs Pakets
 Das Quell Code Verwaltungspaket ist so registriert, dass es von der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Umgebung gefunden werden kann und die unterstützten Funktionen abgefragt werden können. Dies entspricht einem verzögerten Lade Schema, in dem eine Instanz eines Pakets nur erstellt wird, wenn seine Features oder Befehle erforderlich sind oder explizit angefordert werden.

 VSPackages platzieren Informationen in einem Versions spezifischen Registrierungsschlüssel, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\*X. Y*, wobei *X* die Hauptversionsnummer und *Y* die neben Versionsnummer ist. Diese Vorgehensweise bietet die Möglichkeit, eine parallele Installation mehrerer Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zu unterstützen.

 Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Benutzeroberfläche (User Interface, UI) unterstützt die Auswahl aus mehreren installierten Quellcodeverwaltungs-Plug-ins (über das Quellcodeverwaltungs-Adapter Paket) sowie von Quellcodeverwaltungs-VSPackages. Es kann immer nur ein aktives Quellcodeverwaltungs-Plug-in oder ein VSPackage vorhanden sein. Die IDE ermöglicht jedoch den Wechsel zwischen den Quellcodeverwaltungs-Plug-ins und VSPackages über einen automatischen lösungsbasierten Mechanismus zum Austauschen von Paketen. Es gibt einige Anforderungen an den Teil des VSPackage der Quell Code Verwaltung, um diesen Auswahlmechanismus zu aktivieren.

### <a name="registry-entries"></a>Registrierungseinträge
 Ein Quell Code Verwaltungspaket benötigt drei private GUIDs:

- Paket-GUID: Dies ist die Haupt-GUID für das Paket, das die Implementierung der Quell Code Verwaltung enthält (in diesem Abschnitt ID_Package genannt).

- Quellcodeverwaltungs-GUID: Dies ist eine GUID für das Quell Code Verwaltungs-VSPackage, das für die Registrierung beim Visual Studio-Quellcodeverwaltungs-Stub verwendet wird. es wird auch als GUID für die Befehls Benutzeroberfläche verwendet. Die GUID des Quell Code Verwaltungs Dienstanbieter wird unter der GUID der Quell Code Verwaltung registriert. Im Beispiel wird die GUID der Quell Code Verwaltung als ID_SccProvider bezeichnet.

- Quell Code Verwaltungsdienst-GUID: Dies ist die GUID des privaten diensdienstanbieter, der von Visual Studio verwendet wird (in diesem Abschnitt SID_SccPkgService). Zusätzlich muss das Quell Code Verwaltungspaket andere GUIDs für VSPackages, Tool Fenster usw. definieren.

  Die folgenden Registrierungseinträge müssen von einem Quellcodeverwaltungs-VSPackage erstellt werden:

| Schlüsselname | Gewinner |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (Standard) = RG_SZ: {ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (Standard) = RG_SZ: \<Friendly Name des Paket ><br /><br /> Service = RG_SZ: {SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (Standard) = RG_SZ: # \<Resource ID für den lokalisierten Namen ><br /><br /> Package = RG_SZ: {ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Beachten Sie, dass der Schlüssel Name `SourceCodeControl` bereits von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verwendet wird und nicht als Auswahl für \<PackageName > verfügbar ist.) | (Standard) = RG_SZ: {ID_Package} |

## <a name="selecting-a-source-control-package"></a>Auswählen eines Quell Code Verwaltungs Pakets
 Mehrere API-basierte Plug-Ins für Quellcodeverwaltungs-Plug-ins und Quellcodeverwaltungs-VSPackages können gleichzeitig registriert werden. Beim Auswählen eines Quellcodeverwaltungs-Plug-ins oder VSPackages muss sichergestellt werden, dass das Plug-in oder VSPackage von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zum richtigen Zeitpunkt geladen wird und das Laden unnötiger Komponenten verzögert werden kann, bis Sie benötigt werden. Außerdem müssen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die gesamte Benutzeroberfläche aus anderen inaktiven VSPackages entfernen, einschließlich Menü Elemente, Dialogfeldern und Symbolleisten, und die Benutzeroberfläche für das aktive VSPackage anzeigen.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt ein Quellcodeverwaltungs-VSPackage, wenn einer der folgenden Vorgänge ausgeführt wird:

- Die Projekt Mappe wird geöffnet (wenn sich die Projekt Mappe unter Quell Code Verwaltung befindet).

   Wenn eine Projekt Mappe oder ein Projekt unter Quell Code Verwaltung geöffnet wird, bewirkt die IDE, dass das Quell Code Verwaltungs-VSPackage, das für die Projekt Mappe festgelegt wurde, geladen wird.

- Jeder der Menübefehle des VSPackage der Quell Code Verwaltung wird ausgeführt.

  Ein Quellcodeverwaltungs-VSPackage sollte alle benötigten Komponenten nur dann laden, wenn Sie tatsächlich verwendet werden (andernfalls als verzögertes Laden bezeichnet).

### <a name="automatic-solution-based-vspackage-swapping"></a>Automatisches Lösungs basiertes VSPackage-austauschen
 Sie können Quell Code Verwaltungs-VSPackages manuell über das Dialogfeld [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Optionen** unter der Kategorie **Quell** Code Verwaltung austauschen. Automatisches projektmappenbasiertes Paket Austausch bedeutet, dass ein Quell Code Verwaltungspaket, das für eine bestimmte Lösung festgelegt wurde, automatisch auf "aktiv" festgelegt wird, wenn diese Lösung geöffnet wird. Von jedem Quell Code Verwaltungspaket sollten <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> implementiert werden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] behandelt den Wechsel zwischen beiden Quellcodeverwaltungs-Plug-ins (Implementieren der Quellcodeverwaltungs-Plug-in-API) und der Quellcodeverwaltungs-VSPackages.

 Das Quellcodeverwaltungs-Adapter Paket wird verwendet, um zu einem beliebigen API-basierten Plug-in für die Quellcodeverwaltungs-Plug-in zu wechseln. Die Umstellung auf das zwischengeschaltete Quell Code Verwaltungs Adapter-Paket und das festlegen, welches Quellcodeverwaltungs-Plug-in auf "aktiv" oder "inaktiv" gesetzt werden muss, ist für den Benutzer transparent Das Adapter Paket ist immer aktiv, wenn ein Quellcodeverwaltungs-Plug-in aktiv ist. Der Wechsel zwischen zwei Quellcodeverwaltungs-Plug-ins bedeutet, dass die Plug-in-dll einfach geladen und entladen wird. Beim Wechseln zu einem Quellcodeverwaltungs-VSPackage ist jedoch eine Interaktion mit der IDE erforderlich, um das entsprechende VSPackage zu laden.

 Ein Quellcodeverwaltungs-VSPackage wird aufgerufen, wenn eine Projekt Mappe geöffnet wird und der Registrierungsschlüssel für das VSPackage in der Projektmappendatei vorhanden ist. Wenn die Projekt Mappe geöffnet wird, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] den Registrierungs Wert findet und das entsprechende VSPackage für die Quell Code Verwaltung lädt. Alle VSPackages der Quell Code Verwaltung müssen über die oben beschriebenen Registrierungseinträge verfügen. Eine Projekt Mappe, die der Quell Code Verwaltung unterliegt, ist als einem bestimmten Quell Code Verwaltungs-VSPackage zugeordnet. Die Quellcodeverwaltungs-VSPackages müssen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> implementieren, um das automatische Lösungs basierte VSPackage-austauschen zu aktivieren.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio-Benutzeroberfläche zur Paketauswahl und zum Wechseln
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stellt eine Benutzeroberfläche für das Quellcodeverwaltungs-VSPackage und die Plug-in-Auswahl im Dialogfeld **Optionen** unter der Kategorie **Quell** Code Verwaltung bereit. Dadurch kann der Benutzer das aktive Quellcodeverwaltungs-Plug-in oder VSPackage auswählen. Eine Dropdown Liste enthält Folgendes:

- Alle installierten Quell Code Verwaltungs Pakete

- Alle installierten Quellcodeverwaltungs-Plug-ins

- Eine "None"-Option, die die Quell Code Verwaltung deaktiviert.

  Nur die Benutzeroberfläche für die aktive Quell Code Verwaltung ist sichtbar. Die VSPackage-Auswahl blendet die Benutzeroberfläche für das vorherige VSPackage aus und zeigt die Benutzeroberfläche für die neue an. Das aktive VSPackage wird pro Benutzer ausgewählt. Wenn ein Benutzer mehrere Kopien von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gleichzeitig geöffnet hat, kann jeder Benutzer ein anderes aktives VSPackage verwenden. Wenn mehrere Benutzer am gleichen Computer angemeldet sind, kann jeder Benutzer über separate Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] geöffnet verfügen, die jeweils über ein anderes aktives VSPackage verfügen. Wenn mehrere Instanzen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] von einem Benutzer geschlossen werden, wird das Quellcodeverwaltungs-VSPackage, das für die zuletzt geöffnete Projekt Mappe aktiv war, das standardmäßige Quellcodeverwaltungs-VSPackage, das beim Neustart als aktiv festgelegt wird.

  Im Gegensatz zu früheren Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ist ein IDE-Neustart nicht mehr die einzige Möglichkeit zum Wechseln von Quellcodeverwaltungs-VSPackages. Die VSPackage-Auswahl erfolgt automatisch. Zum Wechseln von Paketen sind Windows-Benutzerberechtigungen erforderlich (nicht Administrator oder Poweruser).

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [Features](../../extensibility/internals/source-control-vspackage-features.md)
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackages](../../extensibility/internals/vspackages.md)