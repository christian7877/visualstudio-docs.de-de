---
title: 'Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0832f0e404331e68fe88dfc990c51ed699eca263
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985797"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten
  Sie können die Anpassungsassembly Programm gesteuert aus einem Dokument oder einer Arbeitsmappe entfernen, das Bestandteil einer Anpassung auf Dokument Ebene für Microsoft Office Word oder Microsoft Office Excel ist. Benutzer können dann die Dokumente öffnen und den Inhalt anzeigen, aber eine benutzerdefinierte Benutzeroberfläche, die Sie den Dokumenten hinzufügen, wird nicht angezeigt, und der Code wird nicht ausgeführt.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Sie können die Anpassungsassembly entfernen, indem Sie eine der `RemoveCustomization` Methoden verwenden, die vom [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]bereitgestellt werden. Welche Methode Sie verwenden, hängt davon ab, ob Sie die Anpassung zur Laufzeit entfernen möchten (indem Sie Code in der Anpassung ausführen, während das Word-Dokument oder die Excel-Arbeitsmappe geöffnet ist), oder wenn Sie die Anpassung aus einem geschlossenen Dokument oder einem Dokument entfernen möchten, das i s auf einem Server, auf dem nicht Microsoft Office installiert ist.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>So entfernen Sie die Anpassungsassembly zur Laufzeit

1. In Ihrem Anpassungs Code können Sie die <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A>-Methode (für Word) oder die <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A>-Methode (für Excel) aufzurufen. Diese Methode sollte nur aufgerufen werden, wenn die Anpassung nicht mehr benötigt wird.

     Wo Sie diese Methode im Code aufzurufen, hängt davon ab, wie ihre Anpassung verwendet wird. Wenn Kunden beispielsweise die Features Ihrer Anpassung verwenden, bis Sie bereit sind, das Dokument an andere Clients zu senden, die nur das Dokument selbst (nicht die Anpassung) benötigen, können Sie eine Benutzeroberfläche bereitstellen, die `RemoveCustomization` aufruft, wenn der Kunde darauf klickt. Wenn Ihre Anpassung das Dokument beim ersten Öffnen mit Daten füllt, aber die Anpassung keine anderen Features bereitstellt, auf die direkt von Kunden zugegriffen wird, können Sie RemoveCustomization aufrufen, sobald ihre Anpassung schließt die Initialisierung des Dokuments ab.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>So entfernen Sie die Anpassungsassembly aus einem geschlossenen Dokument oder einem Dokument auf einem Server

1. Fügen Sie in einem Projekt, das keine Microsoft Office benötigt, wie z. b. eine Konsolenanwendung oder ein Windows Forms Projekt, einen Verweis auf die Assembly *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* hinzu.

2. Fügen Sie die folgende **Imports** -oder **using** -Anweisung am Anfang der Codedatei ein.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. Nennen Sie die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>-Methode der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>-Klasse, und geben Sie den projektmappendokumentpfad für den-Parameter an.

     Im folgenden Codebeispiel wird davon ausgegangen, dass Sie die Anpassung aus einem Dokument mit dem Namen *"WordDocument1. docx* entfernen, das sich auf dem Desktop befindet.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer aus, auf dem Sie die Anpassung entfernen möchten. Auf dem Computer muss die Visual Studio 2010-Tools für Office-Laufzeit installiert sein.

## <a name="see-also"></a>Siehe auch
- [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
