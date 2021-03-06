---
title: Erstellen von Websites Palten, Inhaltstypen und Listen für SharePoint | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 538d82794fcecb91e4f13ab6d7718d0bf407b86f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984514"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Erstellen von Websites Palten, Inhaltstypen und Listen für SharePoint
  Visual Studio stellt Projekt Element Vorlagen für viele verschiedene grundlegende SharePoint-Elemente bereit, einschließlich *Listen* und *Inhaltstypen*, die beide Website Spalten (oder *Felder*) enthalten können. Mithilfe der neuen Designer für Inhaltstypen und Listen können Sie diese Elemente einfacher als je zuvor erstellen.

## <a name="site-columns"></a>Websitespalten
 Website Spalten sind eines der grundlegendsten Elemente, die Sie einem SharePoint-Projekt hinzufügen können. Eine Website Spalte stellt einen Datentyp dar, z. b. eine Telefonnummer, einen Kommentar oder den Ortsnamen eines Kontakts in einer Kontaktliste.

 Die neue Site Column-Projekt Element Vorlage macht das Erstellen von Site Spalten einfacher als in der früheren Version von Visual Studio. Nachdem Sie eine neue Website Spalte erstellt haben, können Sie die XML-Datei in der Datei " *Elements. XML* " der Website Spalte so ändern, dass Sie die gewünschten Informationen enthält, z. b. den anzeigen Amen, den Datentyp und die Gruppe, in der die Spalte "Site" in SharePoint angezeigt werden soll. Weitere Informationen zu Site Spalten finden Sie unter [Introduction to Columns (Einführung in Spalten](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14))).

## <a name="content-types-and-lists"></a>Inhaltstypen und Listen
 Inhaltstypen und Listen gehören zu den am häufigsten verwendeten Elementen in SharePoint.

 Ein Inhaltstyp definiert die Metadaten, den Workflow und das Verhalten für eine Kategorie von Elementen in einer SharePoint-Liste oder einer Dokumentbibliothek. Beispielsweise können Sie einen Inhaltstyp für Informationen in einer Kontaktliste oder einer Aufgabenliste erstellen. Ein Kontakt Inhaltstyp kann Spalten wie Name, e-Mail-Adresse, Telefonnummer und Adresse enthalten. Ein Inhaltstyp, den Sie auf Website Ebene definieren, ist unabhängig von einer Liste oder Dokumentbibliothek in der Website. Sie können den gleichen Inhaltstyp mit unterschiedlichen Listen oder Dokument Bibliotheken auf der SharePoint-Website verwenden. Sie können auch mehrere Inhaltstypen für dieselbe Liste oder Dokumentbibliothek verwenden.

 Eine Liste ist eine Sammlung von Informationen in SharePoint, die Sie für andere Personen freigeben können. Listen bestehen aus Zeilen von Spalten, die Daten enthalten. Einige Beispiele für Listen sind: eine Aufgabenliste, eine Liste mit Kontakten und eine Ankündigungsliste.

 Die neuen Inhaltstyp-und Listen-Designer in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] das Erstellen von Website Inhaltstypen und Listen wesentlich einfacher und intuitiver als in der früheren Version von Visual Studio. Die Benutzeroberfläche ermöglicht Ihnen, Inhaltstypen und Listen auf vertraute Weise visuell zu erstellen und ermöglicht das Sortieren und Gruppieren von Daten in Listen und das Verwenden von Gruppen Überschriften. Weitere Informationen zu Inhaltstypen finden Sie unter [Inhaltstypen](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)). Weitere Informationen zu Listen finden Sie unter [Auflisten von Formularen](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) und Listen [Ansichten](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14)).

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Exemplarische Vorgehensweise: Erstellen einer Websites palte, eines Inhaltstyps und einer Liste für SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Veranschaulicht, wie Sie in einem benutzerdefinierten Inhaltstyp verwendete Site Spalten erstellen. Der Inhaltstyp wird dann in einer benutzerdefinierten Liste verwendet.|

## <a name="see-also"></a>Siehe auch
- [Einstieg in die Entwicklung in SharePoint 2010](/sharepoint/dev/)
