---
title: Verwaltete Referenz (Office-Entwicklung in Visual Studio)
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 137031202075d1c646cc7415042dd8d6eab72b78
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985765"
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Verwaltete Referenz (Office-Entwicklung in Visual Studio)
  Dieser Abschnitt enthält eine API-Referenzdokumentation zu Namespaces und Typen, die in Office-Projekten für [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] oder [!INCLUDE[net_v45](includes/net-v45-md.md)]verwendet werden. Eine API-Referenz Dokumentation zu den Namespaces und Typen, die in Office-Projekten verwendet werden, die auf .NET Framework 3,5 abzielen, finden Sie im folgenden Referenz Abschnitt in der Visual Studio-Dokumentation: [verwaltete Referenz (Office-Entwicklung in Visual Studio). )](managed-reference-office-development-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="in-this-section"></a>In diesem Abschnitt
 <xref:Microsoft.Office.Tools>

 Enthält Klassen, die häufig für die Programmierung von Office-Projektmappen verwendet werden. Dazu gehören die Basisklasse für VSTO-Add-Ins, Klassen zum Erstellen von benutzerdefinierten Aufgabenbereichen in VSTO-Add-Ins, Klassen zum Erstellen von Smarttags in Excel- und Word-Projektmappen und Klassen zum Erstellen von Aktionsbereichen in Anpassungen auf Dokumentebene.

 <xref:Microsoft.Office.Tools.Excel>

 Enthält Hoststeuerelemente und Hostelemente, die in Projektmappen für Excel verwendet werden können.

 <xref:Microsoft.Office.Tools.Excel.Controls>

 Enthält Excel-Steuerelemente und Windows Forms-Steuerelemente, die in Projektmappen für Excel verwendet werden können.

 <xref:Microsoft.Office.Tools.Outlook>

 Enthält Klassen, die von VSTO-Add-Ins für Outlook verwendet werden, einschließlich Klassen, die zum Erstellen von benutzerdefinierten Formularbereichen verwendet werden.

 <xref:Microsoft.Office.Tools.Ribbon>

 Enthält Klassen, mit denen programmgesteuert Menübandanpassungen geändert werden, die mithilfe des Menüband-Designers erstellt wurden.

 <xref:Microsoft.Office.Tools.Word>

 Enthält Hoststeuerelemente und Hostelemente, die in Projektmappen für Word verwendet werden können.

 <xref:Microsoft.Office.Tools.Word.Controls>

 Enthält Word-Steuerelemente und Windows Forms-Steuerelemente, die in Projektmappen für Word verwendet werden können.

 <xref:Microsoft.VisualStudio.Tools.Applications>

 Enthält die <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> -Klasse sowie einen Satz zugehöriger zwischengespeicherter Datenklassen. Diese Klassen können verwendet werden, um einige Aspekte von Anpassungen auf Dokumentebene auf Computern zu ändern, auf denen Microsoft Office nicht installiert ist.

 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>

 Enthält die <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> -Schnittstelle (die Sie implementieren können, um für eine Office-Projektmappe eine *Aktion nach der Bereitstellung* zu erstellen), Ausnahmen, die ausgelöst werden können, wenn eine Office-Projektmappe installiert wird, und weitere APIs, die zur Visual Studio-Infrastruktur gehören.

 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>

 Enthält die meisten Ausnahmen, die von [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)]ausgelöst werden können, mehrere Klassen, mit denen Daten in Anpassungen auf Dokumentebene zwischengespeichert werden können, und andere APIs, die Teil der Visual Studio-Infrastruktur sind.

 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>

 Enthält MSBuild-Aufgabenklassen, die zum Erstellen von Office-Projekten verwendet werden.

## <a name="see-also"></a>Siehe auch
- [Übersicht über Visual Studio-Tools für Office-Laufzeit](visual-studio-tools-for-office-runtime-overview.md)
- [Einstieg in &#40;die Office-Entwicklung in Visual Studio&#41;](getting-started-office-development-in-visual-studio.md)
- [Office-Entwicklungs Beispiele und Exemplarische Vorgehensweisen](office-development-samples-and-walkthroughs.md)
- [Entwerfen und Erstellen von Office-Lösungen](designing-and-creating-office-solutions.md)
