---
title: -Build („devenv.exe“)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1766fe22573554b41ebfaa38fbd9e8d6c90c5790
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595760"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Erstellt mithilfe einer angegebenen Projektmappen-Konfigurationsdatei eine Projektmappe oder ein Projekt.

## <a name="syntax"></a>Syntax

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumente

- *SolutionName*

  Erforderlich. Der vollständige Pfad und Name der Projektmappendatei

- *SolnConfigName*

  Dies ist optional. Der Name der Projektmappenkonfiguration (z.B. `Debug` oder `Release`), die zum Erstellen der in *SolutionName* benannten Projektmappe verwendet werden soll. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben (z.B. `Debug|Win32`). Wenn dieses Argument nicht angegeben wird oder eine leere Zeichenfolge (`""`) enthält, verwendet das Tool die aktive Konfiguration der Projektmappe.

- `/Project` *ProjName*

  Dies ist optional. Der Pfad und der Name einer Projektdatei innerhalb der Projektmappe. Sie können einen relativen Pfad vom *SolutionName*-Ordner zur Projektdatei, dem Anzeigenamen des Projekts oder dem vollständigen Pfad und Namen der Projektdatei eingeben.

- `/ProjectConfig` *ProjConfigName*

  Dies ist optional. Der Name der Projektbuildkonfiguration (z.B. `Debug` oder `Release`), die beim Erstellen des benannten Projekts verwendet wird. Wenn mehrere Projektmappenplattformen verfügbar sind, müssen Sie auch die Plattform angeben (z.B. `Debug|Win32`). Wenn dieser Schalter angegeben ist, überschreibt er das Argument *SolnConfigName*.

- `/Out` *OutputFilename*

  Dies ist optional. Der Name der Datei, an die die Ausgabe des Tools gesendet werden soll. Wenn die Datei bereits vorhanden ist, fügt das Tool die Ausgabe an das Ende der Datei an.

## <a name="remarks"></a>Hinweise

- Der Schalter `/Build` führt dieselbe Funktion aus wie der Menübefehl **Projektmappe erstellen** in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE).

- Schließen Sie Zeichenfolgen, die Leerzeichen enthalten, in doppelten Anführungszeichen ein.

- Zusammenfassende Informationen für Builds, inklusive Fehlermeldungen, können im Befehlsfenster oder in einer Protokolldatei, die durch den Schalter `/Out` angegeben wird, angezeigt werden.

- Der Schalter `/Build` erstellt nur Projekte, die seit dem letzten Build geändert wurden. Verwenden Sie stattdessen [/rebuild](../../ide/reference/rebuild-devenv-exe.md), um alle Projekte in einer Projektmappe zu erstellen.

- Wenn Sie die Fehlermeldung **Ungültige Projektkonfiguration** erhalten, stellen Sie sicher, dass Sie eine Projektmappenplattform oder eine Projektplattform angegeben haben (z.B. `Debug|Win32`).

## <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird das Projekt `CSharpWinApp` mithilfe der Projektbuildkonfiguration `Debug` in `MySolution` erstellt.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Siehe auch

- [Erstellen und Bereinigen von Projekten und Projektmappen](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Devenv-Befehlszeilenschalter](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
