---
title: 'CA2105: Array Felder dürfen nicht schreibgeschützt sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7599359899ca4860913b5bc0dd601fd06d9b8b54
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666011"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Arrayfelder dürfen nicht schreibgeschützt sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentliches oder geschütztes Feld, das ein Array enthält, ist als schreibgeschützt deklariert.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Sie den `readonly`-Modifizierer (`ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) auf ein Feld mit einem Array anwenden, kann das Feld nicht geändert werden, um auf ein anderes Array zu verweisen. Allerdings können die in einem schreibgeschützten Feld des Arrays gespeicherten Elemente geändert werden. Code, der Entscheidungen trifft oder Vorgänge ausführt, die auf den Elementen eines schreibgeschützten Arrays basieren, auf das öffentlich zugegriffen werden kann, kann ein ausnutzbares Sicherheitsrisiko enthalten.

 Beachten Sie, dass ein öffentliches Feld auch gegen die Entwurfs Regel [CA1051 verstößt: sichtbare Instanzfelder nicht deklarieren](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um das Sicherheitsrisiko zu beheben, das durch diese Regel identifiziert wird, verlassen Sie sich nicht auf den Inhalt eines schreibgeschützten Arrays, auf das öffentlich zugegriffen werden kann. Es wird dringend empfohlen, eine der folgenden Prozeduren zu verwenden:

- Ersetzen Sie das Array durch eine stark typisierte Auflistung, die nicht geändert werden kann. Weitere Informationen finden Sie unter <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Ersetzen Sie das öffentliche Feld durch eine Methode, die einen Klon eines privaten Arrays zurückgibt. Da sich der Code nicht auf den Klon stützt, besteht keine Gefahr, wenn die Elemente geändert werden.

  Wenn Sie den zweiten Ansatz gewählt haben, ersetzen Sie das Feld nicht durch eine Eigenschaft. Eigenschaften, die Arrays zurückgeben, beeinträchtigen die Leistung. Weitere Informationen finden Sie unter [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es wird dringend davon abgeraten, eine Warnung aus dieser Regel auszuschließen. Es treten fast keine Szenarien auf, in denen der Inhalt eines schreibgeschützten Felds unwichtig ist. Wenn dies in Ihrem Szenario der Fall ist, entfernen Sie den `readonly` Modifizierer, anstatt die Meldung auszuschließen.

## <a name="example"></a>Beispiel
 Dieses Beispiel veranschaulicht die Gefahren, die gegen diese Regel verstoßen. Der erste Teil zeigt eine Beispiel Bibliothek mit dem Typ, `MyClassWithReadOnlyArrayField`, der zwei Felder (`grades` und `privateGrades`) enthält, die nicht sicher sind. Das Feld `grades` ist öffentlich und daher für jeden Aufrufer anfällig. Das Feld `privateGrades` ist privat, aber immer noch anfällig, da es von der `GetPrivateGrades`-Methode an Aufrufer zurückgegeben wird. Das `securePrivateGrades` Feld wird von der `GetSecurePrivateGrades`-Methode auf sichere Weise verfügbar gemacht. Sie wird als privat deklariert, um guten Entwurfs Praktiken zu folgen. Der zweite Teil zeigt Code, der Werte ändert, die in den `grades`-und `privateGrades` Membern gespeichert sind.

 Die Beispiel Klassenbibliothek wird im folgenden Beispiel angezeigt.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Code verwendet die Beispiel Klassenbibliothek, um Sicherheitsprobleme mit Schreib geschütztem Array zu veranschaulichen.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 Die Ausgabe dieses Beispiels lautet wie folgt:

 **Vor der Manipulation: Grades: 90, 90, 90 private Grades: 90, 90, 90 Secure Grades, 90, 90, 90**
**nach Manipulation: Grades: 90, 555, 90 private Grades: 90, 555, 90 Secure Grades, 90, 90, 90**
## <a name="see-also"></a>Siehe auch
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
