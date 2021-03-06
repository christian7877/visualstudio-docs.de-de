---
title: Debuggen mithilfe von vorab abgerufenen Inhalten in UWP-apps | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 28a73974a71df7fa652e4b246043e901df76e94c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730574"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Debuggen von UWP-apps mit vorab abgerufenen Inhalten in Visual Studio

 Damit Ihre UWP-App reaktionsfähiger wird, können Sie anfordern, dass Windows einige Webinhalte wie Webseiten oder Bilder vorab in den [WinInet](/windows/desktop/WinInet/about-wininet) -Cache der APP lädt. Diese Funktion wird als Vorabrufen bezeichnet. Vorabrufen ist besonders effektiv für Inhalte, die beim Starten verwendet werden, aber Sie können auch andere häufig genutzte Inhalte abrufen. Mit den Methoden der [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher)-Klasse können Sie die URIs der gewünschten Inhalte angeben. Beispiele zum Hinzufügen der ContentPrefetcher-Funktionalität zu Apps finden Sie im [Windows SDK-Beispiel zum Vorabrufen von Inhalt](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309).

 Windows bestimmt heuristisch, wann und ob Vorabrufvorgänge stattfinden und welche Ressourcen heruntergeladen werden. Die Heuristik berücksichtigt Netzwerk- und Leistungsbedingungen des Systems für das Konto, den Verwendungsverlauf der App für den Benutzer und die Ergebnisse von früheren Vorabrufversuchen. Mit dem Befehl **Vorabrufen von Windows Store-App auslösen** in Visual Studio zwingen Sie Windows, die ContentPrefetcher-Heuristik zu ignorieren und sämtliche angegebenen Webinhalte vorab zu laden. Das kann nützlich sein, um das Verhalten oder die Leistung der App zu testen, wenn der Inhalt in einem bekannten Zustand (entweder geladen oder nicht geladen) vorabgerufen wird.

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Erzwingen von Vorabladen von Ressourcen, die mit "ContentPrefetcher" angegeben werden
 Dieses Verfahren setzt voraus, dass Sie die ContentPrefetcher-Funktionalität bereits im App-Projekt eingerichtet und die gewünschten Inhalts-URIs zum Vorabladen angegeben haben. Um das Vorabladen von Inhalt zu erzwingen, wenn die angegebenen Ressourcen neu sind oder geändert wurden, müssen Sie die App starten und beenden, bevor Sie den Befehl **Vorabrufen von Windows Store-App auslösen** auswählen. Sie führen zuerst die App aus, um die URIs zu registrieren. Anschließend zwingt der Befehl **Vorabrufen von Windows Store-App auslösen** die ContentPrefetcher-Funktionalität dazu, den Inhalt herunterzuladen und dem Cache hinzuzufügen. Bei nachfolgenden Ausführungen der App können Sie voraussetzen, dass der Inhalt vorab geladen wurde.

1. Starten Sie die App, um die Inhalts-URIs zum Vorabladen in der App zu registrieren. Wählen Sie anschließend im Menü **Debuggen** die Option **Debuggen starten** (Tastenkombination: F5) aus.

2. Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden** (Tastenkombination: UMSCHALT+F5) aus.

3. Wählen Sie im Menü **Debuggen** die Option **Andere Debugziele** und anschließend **Vorabrufen von Windows Store-App auslösen** aus.

   Sie können die App jetzt mit den vorabgerufenen Webressourcen debuggen, testen oder analysieren.

> [!NOTE]
> Wiederholen Sie diese Schritte jedes Mal, wenn Sie die angegebenen Webinhalte ändern oder neue hinzufügen.

## <a name="see-also"></a>Siehe auch
- [Blog Beitrag: Auslösen von Vorabruf für Windows Store-Apps in Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)