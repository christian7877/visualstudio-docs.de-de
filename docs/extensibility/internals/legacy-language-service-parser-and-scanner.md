---
title: Parser und Scanner für Legacy Sprachdienste | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726739"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Parser und Scanner von Legacysprachdiensten
Der Parser ist das Herzstück des sprach Dienstanbieter. Die MPF-Sprachklassen (Managed Package Framework) erfordern einen sprach Parser, um Informationen zum angezeigten Code auszuwählen. Ein Parser trennt den Text in lexikalische Token und identifiziert diese Token nach Typ und Funktionalität.

## <a name="discussion"></a>Diskussion
 Im folgenden finden Sie C# eine-Methode.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 In diesem Beispiel sind die Token die Wörter und Interpunktions Zeichen. Die Arten von Token lauten wie folgt.

|Tokenname|Tokentyp|
|----------------|----------------|
|Namespace, Klasse, Public, void, int|keyword|
|=|operator|
|{ } ( ) ;|Trennzeichen|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|
|MyNamespace|namespace|
|MyClass|Klasse|
|MyFunction|Methode|
|arg1|-Parameter von|
|var1|Lokale Variable|

 Die Rolle des Parsers besteht darin, die Token zu identifizieren. Einige Token können mehr als einen Typ aufweisen. Nachdem der Parser die Token identifiziert hat, kann der Sprachdienst die Informationen verwenden, um hilfreiche Funktionen wie Syntax Hervorhebung, zugehörige Klammern und IntelliSense-Vorgänge bereitzustellen.

## <a name="types-of-parsers"></a>Typen von Parser
 Ein Sprachdienst Parser ist nicht mit einem Parser identisch, der als Teil eines Compilers verwendet wird. Diese Art von Parser muss jedoch sowohl einen Scanner als auch einen Parser wie einen compilerparser verwenden.

- Ein Scanner wird zum Identifizieren von Tokentypen verwendet. Diese Informationen werden zur Syntax Hervorhebung und zum schnellen Identifizieren von Tokentypen verwendet, die andere Vorgänge lösen können, z. b. eine zugehörige Klammer. Dieser Scanner wird durch die <xref:Microsoft.VisualStudio.Package.IScanner>-Schnittstelle dargestellt.

- Ein Parser wird verwendet, um die Funktionen und den Gültigkeitsbereich der Token zu beschreiben. Diese Informationen werden in IntelliSense-Vorgängen verwendet, um Sprachelemente zu identifizieren, wie z. b. Methoden, Variablen, Parameter und Deklarationen, und um Listen von Membern und Methoden Signaturen basierend auf dem Kontext bereitzustellen. Dieser Parser wird auch verwendet, um übereinstimmende sprach Element Paare zu suchen, z. b. geschweifte Klammern und Klammern. Der Zugriff auf diesen Parser erfolgt über die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService>-Klasse.

  Wie Sie einen Scanner und einen Parser für Ihren Sprachdienst implementieren, ist Ihnen überstehen. Es sind verschiedene Ressourcen verfügbar, die beschreiben, wie Parser funktionieren und wie Sie Ihren eigenen Parser schreiben. Außerdem sind mehrere kostenlose und kommerzielle Produkte verfügbar, die bei der Erstellung eines Parsers helfen.

### <a name="the-parsesource-parser"></a>Der ParseSource-Parser
 Anders als bei einem Parser, der als Teil eines Compilers verwendet wird (bei dem die Token in eine Form von ausführbarem Code konvertiert werden), kann ein Sprachdienst Parser aus vielen verschiedenen Gründen und in vielen verschiedenen Kontexten aufgerufen werden. Wie Sie diesen Ansatz in der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService>-Klasse implementieren, ist für Sie von Ihnen. Beachten Sie, dass die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode möglicherweise für einen Hintergrund Thread aufgerufen wird.

> [!CAUTION]
> Die <xref:Microsoft.VisualStudio.Package.ParseRequest>-Struktur enthält einen Verweis auf das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>-Objekt. Dieses <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt kann nicht im Hintergrund Thread verwendet werden. Tatsächlich können viele der Basis-MPF-Klassen nicht im Hintergrund Thread verwendet werden. Hierzu gehören die <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Klassen und jede andere Klasse, die direkt oder indirekt mit der Ansicht kommuniziert.

 Dieser Parser analysiert in der Regel die gesamte Quelldatei, wenn Sie zum ersten Mal aufgerufen wird, oder wenn der analysieren Reason-Wert <xref:Microsoft.VisualStudio.Package.ParseReason> angegeben wird. Nachfolgende Aufrufe der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode verarbeiten einen kleinen Teil des analysierten Codes und können viel schneller ausgeführt werden, indem die Ergebnisse des vorherigen vollständigen Analyse Vorgangs verwendet werden. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode kommuniziert die Ergebnisse des-erteilungsvorgangs über das <xref:Microsoft.VisualStudio.Package.AuthoringSink>-und <xref:Microsoft.VisualStudio.Package.AuthoringScope>-Objekt. Das <xref:Microsoft.VisualStudio.Package.AuthoringSink>-Objekt wird verwendet, um Informationen für einen bestimmten erfassenden Grund zu erfassen, z. b. Informationen zu den Spannen von übereinstimmenden geschweiften Klammern oder Methoden Signaturen, die Parameterlisten aufweisen. Der <xref:Microsoft.VisualStudio.Package.AuthoringScope> stellt Auflistungen von Deklarationen und Methoden Signaturen bereit und unterstützt auch die Option Gehe zu erweiterter Bearbeitung (gehe**zu Definition**, **Gehe zu Deklaration**, **Gehe zu Referenz**).

### <a name="the-iscanner-scanner"></a>Der iScanner-Scanner
 Außerdem müssen Sie einen Scanner implementieren, der <xref:Microsoft.VisualStudio.Package.IScanner> implementiert. Da diese Überprüfung jedoch zeilenweise durch die <xref:Microsoft.VisualStudio.Package.Colorizer>-Klasse funktioniert, ist Sie in der Regel einfacher zu implementieren. Am Anfang jeder Zeile gibt das MPF der <xref:Microsoft.VisualStudio.Package.Colorizer>-Klasse einen Wert an, der als Zustands Variable verwendet werden soll, die an den Scanner übermittelt wird. Am Ende jeder Zeile gibt der Scanner die aktualisierte Zustands Variable zurück. Der MPF speichert diese Zustandsinformationen für jede Zeile zwischen, sodass die Überprüfung von einer beliebigen Zeile aus beginnen kann, ohne am Anfang der Quelldatei beginnen zu müssen. Diese schnelle Überprüfung einer einzelnen Zeile ermöglicht es dem Editor, dem Benutzer schnelles Feedback zu geben.

## <a name="parsing-for-matching-braces"></a>Auswerten von übereinstimmenden geschweiften Klammern
 Dieses Beispiel zeigt die Ablauf Steuerung, mit der eine schließende geschweifte Klammer abgeglichen wird, die der Benutzer eingegeben hat. In diesem Prozess wird auch der Scanner verwendet, der für die Farbgebung verwendet wird, um den Tokentyp zu bestimmen und ob das Token einen Vorgang zum Überprüfen der Klammer auslöst. Wenn der-Aufruf gefunden wird, wird die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode aufgerufen, um die passende geschweifter Klammer zu suchen. Schließlich werden die beiden geschweiften Klammern hervorgehoben.

 Obwohl geschweifte Klammern in den Namen von Triggern und Analyse Gründen verwendet werden, ist dieser Prozess nicht auf die eigentlichen geschweiften Klammern beschränkt. Alle Paare von Zeichen, die als entsprechendes Paar angegeben werden, werden unterstützt. Beispiele hierfür sind (und), \< und > und [und].

 Angenommen, der Sprachdienst unterstützt passende geschweifte Klammern.

1. Der Benutzer gibt eine schließende geschweifte Klammer (}) ein.

2. Die geschweifte Klammer wird am Cursor in der Quelldatei eingefügt, und der Cursor wird um eins erweitert.

3. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>-Methode in der <xref:Microsoft.VisualStudio.Package.Source>-Klasse wird mit der typisierten schließenden geschweifte Klammer aufgerufen.

4. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>-Methode ruft die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>-Methode in der <xref:Microsoft.VisualStudio.Package.Source>-Klasse auf, um das Token an der Position direkt vor der aktuellen Cursorposition abzurufen. Dieses Token entspricht der typisierten schließenden Klammer).

    1. Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>-Methode ruft die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>-Methode für das <xref:Microsoft.VisualStudio.Package.Colorizer>-Objekt auf, um alle Token in der aktuellen Zeile abzurufen.

    2. Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>-Methode ruft die <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>-Methode für das <xref:Microsoft.VisualStudio.Package.IScanner>-Objekt mit dem Text der aktuellen Zeile auf.

    3. Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>-Methode ruft wiederholt die <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>-Methode für das <xref:Microsoft.VisualStudio.Package.IScanner>-Objekt auf, um alle Token aus der aktuellen Zeile zu erfassen.

    4. Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>-Methode ruft eine private Methode in der <xref:Microsoft.VisualStudio.Package.Source>-Klasse auf, um das Token abzurufen, das die gewünschte Position enthält, und übergibt in der Liste der Token, die von der <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>-Methode abgerufen werden.

5. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>-Methode sucht nach einem tokenauslöserflag <xref:Microsoft.VisualStudio.Package.TokenTriggers> auf dem Token, das von der <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>-Methode zurückgegeben wird. Das heißt, das Token, das die schließende geschweifte Klammer darstellt.

6. Wenn das auslöserflag von <xref:Microsoft.VisualStudio.Package.TokenTriggers> gefunden wird, wird die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>-Methode in der <xref:Microsoft.VisualStudio.Package.Source>-Klasse aufgerufen.

7. Die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>-Methode startet einen Analyse Vorgang mit dem Wert "Analyse Grund" <xref:Microsoft.VisualStudio.Package.ParseReason>. Dieser Vorgang ruft letztendlich die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService>-Klasse auf. Wenn die asynchrone Analysierung aktiviert ist, tritt dieser <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode in einem Hintergrund Thread auf.

8. Wenn der Erstellungs Vorgang abgeschlossen ist, wird ein interner Abschluss Handler (auch als Rückruf Methode bezeichnet) namens "`HandleMatchBracesResponse`" in der <xref:Microsoft.VisualStudio.Package.Source>-Klasse aufgerufen. Dieser Aufrufe erfolgt automatisch durch die <xref:Microsoft.VisualStudio.Package.LanguageService> Basisklasse, nicht durch den Parser.

9. Die `HandleMatchBracesResponse`-Methode ruft eine Liste von spannen aus dem <xref:Microsoft.VisualStudio.Package.AuthoringSink>-Objekt ab, das im <xref:Microsoft.VisualStudio.Package.ParseRequest>-Objekt gespeichert ist. (Eine Spanne ist eine <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>-Struktur, die einen Bereich von Linien und Zeichen in der Quelldatei angibt.) Diese Liste mit spannen enthält in der Regel zwei Spannen, jeweils eine für die öffnenden und schließenden geschweiften Klammern.

10. Die `HandleBracesResponse`-Methode ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>-Methode für das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>-Objekt auf, das im <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt gespeichert ist. Hierdurch werden die angegebenen spannen hervorgehoben.

11. Wenn die <xref:Microsoft.VisualStudio.Package.LanguagePreferences>-Eigenschaft <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> aktiviert ist, ruft die `HandleBracesResponse`-Methode den Text ab, der von der passenden Spanne eingeschlossen wird, und zeigt die ersten 80 Zeichen dieser Spanne in der Statusleiste an. Dies funktioniert am besten, wenn die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode das Language-Element enthält, das mit dem passenden Paar übereinstimmt. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>-Eigenschaft.

12. Ausgeführt.

### <a name="summary"></a>Zusammenfassung
 Der Vorgang der passenden geschweiften Klammern ist in der Regel auf einfache Paare von Sprachelementen beschränkt. Komplexere Elemente, wie z. b. übereinstimmende drei Elemente ("`if(...)`", "`{`" und "`}`" oder "`else`", "`{`" und "`}`"), können als Teil eines Wort Vervollständigungs Vorgangs hervorgehoben werden. Wenn z. b. das Wort "Else" beendet ist, kann die entsprechende "`if`"-Anweisung hervorgehoben werden. Wenn eine Reihe von `if` / `else if`-Anweisungen vorhanden wäre, können alle diese mithilfe desselben Mechanismus hervorgehoben werden, der mit geschweiften Klammern übereinstimmt. Die <xref:Microsoft.VisualStudio.Package.Source>-Basisklasse unterstützt diese bereits wie folgt: der Scanner muss den tokenauslöserwert zurückgeben <xref:Microsoft.VisualStudio.Package.TokenTriggers> in Kombination mit dem <xref:Microsoft.VisualStudio.Package.TokenTriggers> des Auslösers für das Token vor der Cursorposition zurückgeben.

 Weitere Informationen finden Sie unter [Abgleichen von Klammern in einem Legacy Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Auswerten der farbliche Farbgebung
 Die farbliche Farbgebung ist einfach. identifizieren Sie einfach den Typ des Tokens, und geben Sie Farbinformationen zu diesem Typ zurück. Die <xref:Microsoft.VisualStudio.Package.Colorizer>-Klasse fungiert als Vermittler zwischen dem Editor und dem Scanner, um Farbinformationen zu jedem Token bereitzustellen. Die <xref:Microsoft.VisualStudio.Package.Colorizer>-Klasse verwendet das <xref:Microsoft.VisualStudio.Package.IScanner>-Objekt, um die Farbgebung einer Linie und die Erfassung von Zustandsinformationen für alle Zeilen in der Quelldatei zu unterstützen. In den MPF-Sprachdienst Klassen muss die <xref:Microsoft.VisualStudio.Package.Colorizer>-Klasse nicht überschrieben werden, da Sie nur über die <xref:Microsoft.VisualStudio.Package.IScanner>-Schnittstelle mit dem Scanner kommuniziert. Das Objekt, das die <xref:Microsoft.VisualStudio.Package.IScanner>-Schnittstelle implementiert, wird durch Überschreiben der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>-Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService>-Klasse bereitgestellt.

 Der <xref:Microsoft.VisualStudio.Package.IScanner> Scanner wird eine Zeile des Quellcodes über die <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>-Methode übergeben. Aufrufe der <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>-Methode werden wiederholt, um das nächste Token in der Zeile abzurufen, bis die Zeile Token erreicht. Zur Farbgebung behandelt der MPF den gesamten Quellcode als Sequenz von Zeilen. Daher muss die Überprüfung in der Lage sein, mit der Quelle zu umgehen, die als Zeilen bereit steht. Darüber hinaus kann jede Zeile jederzeit an die Überprüfung übermittelt werden, und die einzige Garantie besteht darin, dass der Scanner die Zustands Variable von der Zeile empfängt, bevor die Zeile angezeigt wird.

 Die <xref:Microsoft.VisualStudio.Package.Colorizer>-Klasse wird auch verwendet, um tokentrigger zu identifizieren. Diese Trigger weisen den MPF darauf hin, dass ein bestimmtes Token einen komplexeren Vorgang initiieren kann, wie z. b. die Wortvervollständigung oder entsprechende geschweifte Klammern. Da die Identifizierung solcher Trigger schnell erfolgen muss und an einem beliebigen Speicherort erfolgen muss, eignet sich der Scanner am besten für diese Aufgabe.

 Weitere Informationen finden Sie unter [Syntax Farbgebung in einem Legacy Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Die Funktionalität und der Bereich werden verarbeitet.
 Das Parsen von Funktionen und Bereichen erfordert mehr Aufwand als nur die Art der gefundenen Token zu identifizieren. Der Parser muss nicht nur den Tokentyp, sondern auch die Funktionalität identifizieren, für die das Token verwendet wird. Ein Bezeichner ist beispielsweise nur ein Name, aber in Ihrer Sprache kann ein Bezeichner der Name einer Klasse, eines Namespaces, einer Methode oder einer Variablen sein, je nach Kontext. Der allgemeine Typ des Tokens kann ein Bezeichner sein, aber der Bezeichner kann auch andere Bedeutungen haben, je nachdem, was er ist und wo er definiert ist. Diese Identifikation erfordert, dass der Parser ausführlichere Informationen zu der Sprache hat, die analysiert wird. An dieser Stelle kommt die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse ins Spiel. Die <xref:Microsoft.VisualStudio.Package.AuthoringSink>-Klasse sammelt Informationen über Bezeichner, Methoden, übereinstimmende Sprachpaare (z. b. geschweifte Klammern und Klammern) und sprach Übersichten (ähnlich wie Sprachpaare, mit dem Unterschied, dass es drei Teile gibt, z. b. "`foreach()`" "`{`" und "`}`"). . Darüber hinaus können Sie die <xref:Microsoft.VisualStudio.Package.AuthoringSink>-Klasse außer Kraft setzen, um die Code Identifizierung zu unterstützen, die bei der frühen Validierung von Haltepunkten verwendet wird, sodass der Debugger nicht geladen werden muss, und das Fenster Auto **-Debugging,** das lokale Variablen und Parameter anzeigt. automatisch beim Debuggen eines Programms und erfordert, dass der Parser zusätzlich zu den vom Debugger vorgegebenen lokalen Variablen und Parametern entsprechende lokale Variablen und Parameter identifiziert.

 Das <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt wird als Teil des <xref:Microsoft.VisualStudio.Package.ParseRequest>-Objekts an den Parser übergeben, und jedes Mal, wenn ein neues <xref:Microsoft.VisualStudio.Package.ParseRequest>-Objekt erstellt wird, wird ein neues <xref:Microsoft.VisualStudio.Package.AuthoringSink>-Objekt erstellt. Außerdem muss die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>-Methode ein <xref:Microsoft.VisualStudio.Package.AuthoringScope>-Objekt zurückgeben, das verwendet wird, um verschiedene IntelliSense-Vorgänge zu verarbeiten. Das <xref:Microsoft.VisualStudio.Package.AuthoringScope>-Objekt verwaltet eine Liste der Deklarationen und eine Liste der Methoden, von denen je nach dem Grund für die-Verarbeitung eine Liste der-Methoden aufgefüllt wird. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse muss implementiert werden.

## <a name="see-also"></a>Siehe auch
- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)
- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)