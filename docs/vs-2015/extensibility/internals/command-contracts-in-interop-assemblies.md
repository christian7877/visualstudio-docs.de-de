---
title: Befehl Verträge im Interop-Assemblys | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195125"
---
# <a name="command-contracts-in-interop-assemblies"></a>Befehlsverträge in Interop-Assemblys
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Basisvertrag für die Behandlung von Befehlen über die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle ist, dass die Umgebung Ruft die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode, um zu bestimmen, ob der Befehl unterstützt wird, und es unterstützt wird, um dessen Zustand und den Text zu bestimmen. Anschließend ruft die Umgebung die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode zum Ausführen des Befehls.  
  
 Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode erfolgt genauso wie für alle Befehle. Weitere Kommunikation, bei Bedarf (z. B. mit Dropdownlisten), wird durch den Aufruf verwaltet die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Methode mit entsprechenden Parametern. Die Interpretation dieser Parameter hängt von den angegebenen Befehl ab.  
  
 Wenn das Ziel des Befehls die Werte in der Output-Parameter zurückgibt, ist der Aufrufer immer verantwortlich für das Freigeben von Ressourcen, die zugeordnet war. Da dieser Parameter auf einen Variant-Wert ist, gibt die Variante Löschen der Ressourcen frei.  
  
 In Fällen, in denen Befehle ausgeführt in einem Fenster "Aufrufhierarchie werden müssen" die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle muss verwendet werden. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> Schnittstelle verfügt über ein ähnlicher Vertrag mit ähnlichen Methoden: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## <a name="see-also"></a>Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehlsrouting in VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementation (Implementierung)](../../extensibility/internals/command-implementation.md)
