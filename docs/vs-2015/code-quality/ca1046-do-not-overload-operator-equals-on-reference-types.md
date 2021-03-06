---
title: 'CA1046: Gleichheits Operator für Referenztypen nicht überladen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 519faf2d49cb74d60d342d6bcf449f211076b0b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661082"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Gleichheitsoperator für Referenztypen nicht überladen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Gleichheits Operator wird von einem öffentlichen oder einem anderen öffentlichen Verweistyp überladen.

## <a name="rule-description"></a>Regelbeschreibung
 Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend. Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die Implementierung des Gleichheits Operators.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sich der Referenztyp wie ein integrierter Werttyp verhält. Wenn es sinnvoll ist, eine Addition oder Subtraktion für Instanzen des Typs durchzuführen, ist es wahrscheinlich richtig, den Gleichheits Operator zu implementieren und die Verletzung zu unterdrücken.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird das Standardverhalten beim Vergleichen von zwei verweisen veranschaulicht.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung vergleicht einige Verweise.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **a = New (2, 2) und b = New (2, 2) sind gleich? Nein** 
**c und a sind gleich? Ja** 
**b und a sind = =? Keine** 
**c und a sind = =? Ja**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Siehe auch
 [Gleichheits Operatoren](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a) <xref:System.Object.Equals%2A?displayProperty=fullName>
