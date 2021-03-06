---
title: Workflow-Designer-Write-Aktivität-Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e3b4da69a2d9154f36e42d3b20657e204767872
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593023"
---
# <a name="writeline-activity-designer"></a>WriteLine-Aktivitätsdesigner

Der **beschreiteline** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.WriteLine>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-writeline-activity"></a>Die WriteLine-Aktivität

Die <xref:System.Activities.Statements.WriteLine>-Aktivität schreibt Text in ein angegebenes <xref:System.IO.TextWriter>-Objekt. Wenn kein <xref:System.IO.TextWriter> angegeben wird, schreibt <xref:System.Activities.Statements.WriteLine> den Text in die Konsole.

### <a name="using-the-writeline-activity-designer"></a>Verwenden des WriteLine-Aktivitätsdesigners

Greifen Sie in der Kategorie **primitive** der **Toolbox**auf den **Write** -Aktivität-Designer zu. Der **beschreibbare** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.WriteLine>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert WriteLine erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann in der Kopfzeile des **Schreib** -oder-Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-writeline-properties"></a>Die WriteLine-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.WriteLine>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaften Raster bearbeitet werden, und einige von Ihnen können auf Workflow-Designer Oberfläche bearbeitet werden.

|Eigenschaftsname|Erforderlich|Verwendungs-|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der Anzeigename der <xref:System.Activities.Statements.WriteLine>-Aktivität. Der Standardwert lautet WriteLine. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|Falsch|Der zu schreibende Text. Um die-Eigenschaft festzulegen, geben Sie im **Textfeld** im **Schreib** Weise-Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|Falsch|Die <xref:System.IO.TextWriter>-Instanz, an die die <xref:System.Activities.Statements.WriteLine>-Aktivität den <xref:System.Activities.Statements.WriteLine.Text%2A>-Text ausgibt. Der Standardwert ist die Konsole.|

## <a name="see-also"></a>Siehe auch

- [Primitive](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
