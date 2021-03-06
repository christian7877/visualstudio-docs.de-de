---
title: Lokalisieren von VSIX-Paketen | Microsoft-Dokumentation
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 171c8635c2d6db2c346fb836701e630812ecbb28
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186445"
---
# <a name="localizing-vsix-packages"></a>Lokalisieren von VSIX-Paketen

Sie können ein VSIX-Paket lokalisieren, indem Sie für jede Zielsprache eine *Erweiterung. vsixlangpack* -Datei erstellen und diese dann in den richtigen Ordner einfügen. Wenn ein lokalisiertes Paket installiert wird, wird der lokalisierte Name der Erweiterung sowie eine lokalisierte Beschreibung angezeigt. Wenn Sie eine lokalisierte Lizenzdatei oder eine URL angeben, die auf lokalisierte Informationen verweist, werden diese ebenfalls angezeigt.

Wenn Ihr VSIX-Paket ein VSPackage enthält, das Menübefehle oder eine andere Benutzeroberfläche hinzufügt, finden Sie unter [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Informationen zum Lokalisieren der neuen Benutzeroberflächen Elemente.

## <a name="directory-structure"></a>Verzeichnisstruktur

 Wenn ein Benutzer eine Erweiterung installiert, prüft **Extensions und Updates** die oberste Ebene des VSIX-Pakets auf einen Ordner, dessen Name mit dem Visual Studio-Gebiets Schema des Ziel Computers übereinstimmt. Wenn **Erweiterungen und Updates** eine *vsixlangpack* -Datei im Ordner finden, werden die lokalisierten Werte in dieser Datei durch die entsprechenden Werte in der *vsixmanifest* -Datei ersetzt. Diese Werte werden angezeigt, wenn die Erweiterung installiert wird. Das folgende Beispiel zeigt die Verzeichnisstruktur für ein VSIX-Paket, das in Spanisch (es-es) und Französisch (fr-FR) lokalisiert wird.

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Die von VSIX unterstützten Projektvorlagen in der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generieren ein VSIX-Manifest und nennen es " *Source. Extension. vsixmanifest*". Wenn das Projekt von Visual Studio erstellt wird, wird der Inhalt dieser Datei in das vsixmanifest-Erweiterungs Element im VSIX-Paket kopiert.

## <a name="the-extensionvsixlangpack-file"></a>Die Dateierweiterung. vsixlangpack

Die *Extension. vsixlangpack* -Datei folgt dem [VSIX-Sprachpaket Schema 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Dieses Schema verfügt über eine `PackageLanguagePackManifest`, der unmittelbar ein `Metadata` untergeordnetes Element folgt. Das Metadatenelement kann bis zu 6 untergeordnete Elemente, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`und `Icon`enthalten. Diese untergeordneten Elemente entsprechen den untergeordneten Elementen `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`und `Icon` des `Metadata`-Elements der *Extension. vsixmanifest* -Datei.

Wenn Sie eine vsixlangpack-Datei erstellen, müssen Sie die `Include in Vsix`-Eigenschaft auf `true`festlegen. Andernfalls wird der lokalisierte Installations Text ignoriert.

### <a name="to-set-the-include-in-vsix-property"></a>So legen Sie die Eigenschaft in VSIX einschließen fest

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die Dateierweiterung. vsixlangpack, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie im **Eigenschaften Raster**auf **in VSIX einschließen**, und legen Sie dessen Wert auf `true`fest.

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung

Das folgende Beispiel zeigt relevante Teile einer Datei *Erweiterung. vsixmanifest* . Die Datei enthält auch die entsprechende Datei *Erweiterung. vsixlangpack* für Spanisch. Die Werte aus dem Language Pack ersetzen die Werte aus dem Manifest, wenn das Visual Studio-Gebiets Schema des Ziel Computers auf Spanisch festgelegt ist.

### <a name="code"></a>Code

- [*Extension. vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Extension. vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Siehe auch

|Titel|Beschreibung|
|-----------|-----------------|
|[VSIX-Sprachpaket Schema 2,0 Referenz](vsix-language-pack-schema-2-0-reference.md)|Ein VSIX-Sprachpaket beschreibt die Lokalisierungs Informationen einer VSIX-Bereitstellungs Datei.|
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Struktur und den Inhalt eines VSIX-Pakets.|
|[Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)|Zeigt, wie andere Textressourcen in einer Erweiterung lokalisiert werden.|