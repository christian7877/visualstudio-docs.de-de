---
title: Benutzeroberfläche der Projekteigenschaften | Microsoft-Dokumentation
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a83e5c9fb633322da536e62f1ba03484b965b162
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252355"
---
# <a name="project-property-user-interface"></a>Benutzeroberfläche für Projekteigenschaften

Ein Projekt Untertyp kann die Elemente im Dialogfeld **Eigenschaften Seiten** des Projekts verwenden, wenn Sie vom Basisprojekt bereitgestellt werden, schreibgeschützte Steuerelemente und ganze Seiten als Bereitstellung ausblenden oder schreibgeschützte Steuerelemente und ganze Seiten oder Projekt Untertyp spezifische Seiten zum Dialogfeld **Eigenschaften Seiten** hinzufügen. Chens.

## <a name="extending-the-project-property-dialog-box"></a>Erweitern der Projekt Eigenschaft (Dialog Feld)

Ein Projekt Untertyp implementiert Automatisierungsextenders und Projektkonfigurations-Such Objekte. Diese Extender implementieren die <xref:EnvDTE.IFilterProperties> -Schnittstelle, um bestimmte Eigenschaften als ausgeblendet oder schreibgeschützt zu gestalten. Im Dialogfeld **Eigenschaften Seiten** des Basis Projekts, das vom Basisprojekt implementiert wird, wird die von den Automatisierungsextendern ausgeführte Filterung berücksichtigt.

Der Prozess der Erweiterung des Dialog Felds " **Projekteigenschaften** " wird im folgenden beschrieben:

- Das Basisprojekt Ruft die Extender aus dem Projekt Untertyp ab, indem die <xref:EnvDTE80.IInternalExtenderProvider> -Schnittstelle implementiert wird. Diese Schnittstelle wird durch die Such-, Projekt Automation-und Projektkonfigurations-Such Objekte des Basis Projekts implementiert.

- Die Implementierung von <xref:EnvDTE80.IInternalExtenderProvider> für das Project Browse-Objekt und das Project Automation-Objekt Delegat <xref:EnvDTE80.IInternalExtenderProvider> zur Implementierung des Projekt unter typaggregators `QueryInterface` (d. h. <xref:EnvDTE80.IInternalExtenderProvider> für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Project-Objekt).

- Das Basisobjekt für die Projekt Konfigurations Suche <xref:EnvDTE80.IInternalExtenderProvider> implementiert auch, um den Automation-Extender direkt aus dem Konfigurationsobjekt des Projekt unter Typs zu übertragen. Die Implementierung delegiert an die <xref:EnvDTE80.IInternalExtenderProvider> Schnittstelle, die durch den Projekt Untertyp Aggregator implementiert wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>Gibt das-Objekt zurück, das <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> vom Projekt Konfigurations Such Objekt implementiert wird.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, auch vom Projekt Konfigurations Such Objekt implementiert, gibt das <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> -Objekt zurück.

- Mit einem Projekt Untertyp können die entsprechenden CATIDs für die verschiedenen erweiterbaren Objekte des Basis Projekts zur Laufzeit ermittelt werden, indem die folgenden <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> Werte abgerufen werden:

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_ExtObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_BrowseObjectCATID>

  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2.VSHPROPID_CfgBrowseObjectCATID>

Zum Ermitteln der CATIDs für den Projektbereich ruft der Projekt Untertyp die oben genannten Eigenschaften für [vsitemid ab. Der Stamm aus der](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) `VSITEMID typedef`. Ein Projekt Untertyp kann auch steuern, welche **Eigenschaften Seiten** -Dialogfeld Seiten für das Projekt angezeigt werden, und zwar sowohl von der Konfiguration abhängig als auch von der Konfiguration unabhängig voneinander. Einige Projekt Untertypen müssen möglicherweise integrierte Seiten entfernen und Projekt Untertyp spezifische Seiten hinzufügen. Um dies zu ermöglichen, ruft das verwaltete Client Projekt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> -Methode für die folgenden Eigenschaften auf:

- `VSHPROPID_PropertyPagesCLSIDList`– eine durch Semikolons getrennte Liste von CLSIDs von Konfigurations unabhängigen Eigenschaften Seiten.

- `VSHPROPID_CfgPropertyPagesCLSIDList —`eine durch Semikolons getrennte Liste von CLSIDs von Konfigurations abhängigen Eigenschaften Seiten.

Da der Projekt Untertyp das <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt aggregiert, kann es die Definition dieser Eigenschaften überschreiben, um zu steuern, welche Eigenschaften **Seiten** Dialogfelder angezeigt werden. Der Projekt Untertyp kann diese Eigenschaften aus dem inneren Basisprojekt abrufen und dann ggf. CLSIDs hinzufügen oder entfernen.

Neue Eigenschaften Seiten, die durch einen Projekt Untertyp hinzugefügt wurden, werden einem Projekt Konfigurations Such Objekt aus der Basisprojekt Implementierung übergeben. Dieses Objekt zum Durchsuchen von Projekt Konfigurationen unterstützt Automatisierungs Erweiterungen. Weitere Informationen zu automationextenders finden Sie unter [implementieren und Verwenden von automatisierungsexextender](https://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Die Eigenschaften Seiten, die durch den Projekt Untertyp <xref:EnvDTE.Project.Extender%2A> implementiert werden, rufen Ihr eigenes Projekt Untertypen-Konfigurations Such Objekt ab, das das Konfigurations Such Objekt des Basis Projekts erweitert.

## <a name="see-also"></a>Siehe auch

- <xref:EnvDTE.IFilterProperties>
- [Dialog Feld "Eigenschaften Seiten"](/previous-versions/visualstudio/visual-studio-2010/as5chysf(v=vs.100))
