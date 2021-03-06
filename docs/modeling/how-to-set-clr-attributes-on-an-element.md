---
title: 'Gewusst wie: Festlegen von CLR-Attributen für ein Element'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f943f9713e4432f0b06242a2f66acae6b390e5cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748368"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Gewusst wie: Festlegen von CLR-Attributen für ein Element
Benutzerdefinierte Attribute sind spezielle Attribute, die Domänen Elementen, Formen, Connectors und Diagrammen hinzugefügt werden können. Sie können jedes Attribut hinzufügen, das von der `System.Attribute`-Klasse erbt.

### <a name="to-add-a-custom-attribute"></a>Hinzufügen eines benutzerdefinierten Attributs

1. Wählen Sie im **DSL-Explorer**das Element aus, dem Sie ein benutzerdefiniertes Attribut hinzufügen möchten.

2. Klicken Sie im **Eigenschaften** Fenster neben der Eigenschaft **benutzerdefinierte Attribute** auf das Symbol zum Durchsuchen ( **..** .).

     Das Dialogfeld **Attribute bearbeiten** wird geöffnet.

3. Klicken Sie in der Spalte **Name** auf **\<add Attribut >** , und geben Sie den Namen des Attributs ein. Drücken Sie die EINGABETASTE.

4. Die Zeile unter dem Attributnamen zeigt Klammern an. Geben Sie in dieser Zeile einen Parametertyp für das Attribut ein (z. b. `string`), und drücken Sie dann die EINGABETASTE.

5. Geben Sie in der Spalte **Name Property (Name** ) einen geeigneten Namen ein, z. b. `MyString`.

6. Klicken Sie auf **OK**.

     Die Eigenschaft **benutzerdefinierte Attribute** zeigt nun das Attribut im folgenden Format an:

     `[` *attributeName* `(` *Parametername* `=` *Type* `)]`

## <a name="see-also"></a>Siehe auch

- [Domain-Specific Language Tools Glossary (Glossar zu DSL-Tools)](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)