---
title: 'CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4c105a1224c405d0be9d74ac6500c875df28604d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604033"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059: Member sollten bestimmte konkrete Typen nicht verfügbar machen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Member ist ein bestimmter konkreter Typ oder macht bestimmte konkrete Typen über einen seiner Parameter oder Rückgabewerte verfügbar. Zurzeit meldet diese Regel die verfügbar machung der folgenden konkreten Typen:

- Ein von <xref:System.Xml.XmlNode?displayProperty=fullName> abgeleiteter Typ.

## <a name="rule-description"></a>Regelbeschreibung
 Ein konkreter Typ ist ein Typ, der eine vollständige Implementierung aufweist und deshalb instanziiert werden kann. Um die weit verbreitete Verwendung des Members zuzulassen, ersetzen Sie den konkreten Typ durch die vorgeschlagene Schnittstelle. Dadurch kann der Member jeden Typ akzeptieren, der die-Schnittstelle implementiert oder verwendet wird, wenn ein Typ erwartet wird, der die-Schnittstelle implementiert.

 In der folgenden Tabelle sind die gezielten konkreten Typen und deren vorgeschlagene Ersetzung aufgeführt.

|Konkreter Typ|Ersetzung|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName><br /><br /> Durch die Verwendung der-Schnittstelle wird der Member von einer bestimmten Implementierung einer XML-Datenquelle entkoppelt.|

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den konkreten Typ in die vorgeschlagene Schnittstelle.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Nachricht aus dieser Regel zu unterdrücken, wenn die vom konkreten Typ bereitgestellte spezifische Funktionalität erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1011: Basistypen als Parameter übergeben](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)
