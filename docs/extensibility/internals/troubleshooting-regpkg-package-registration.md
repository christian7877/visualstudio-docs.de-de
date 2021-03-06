---
title: Problembehandlung bei der regpkg-Paket Registrierung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 386a1a17c036207d122e4b3c7cb142a628dcfe38
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722279"
---
# <a name="troubleshooting-regpkg-package-registration"></a>Problembehandlung bei der Registrierung des RegPkg-Pakets
> [!NOTE]
> Die bevorzugte Methode zum Registrieren von Paketen in Visual Studio besteht darin, pkgdef-Dateien zu verwenden. Dies ermöglicht die Erweiterungs Bereitstellung, ohne auf die Systemregistrierung zugreifen zu müssen. Pkgdef-Dateien werden mit dem [Dienstprogramm](../../extensibility/internals/createpkgdef-utility.md)"|" erstellt.

 Wenn Sie ein Paket mithilfe von regpkg in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrieren möchten, müssen Sie die Version von regpkg verwenden, die für das Paket geeignet ist.

## <a name="regpkg-versions-related-to-package-versions"></a>Regpkg-Versionen im Zusammenhang mit Paketversionen
 Es gibt zwei Versionen von regpkg. Eine Version ist in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enthalten. Verwenden Sie diese Version zum Registrieren von Paketen, die mit einer der folgenden Assemblys erstellt wurden:

1. Microsoft. visualstudioshell. 9.0. dll

2. Microsoft. visualstudioshell. 10.0. dll

3. Microsoft. visualstudioshell. 11.0. dll

   Pakete, die mithilfe der früheren Microsoft. VisualStudio. Shell. dll-Assembly erstellt wurden, können nicht registriert werden.

   Mit der früheren Version von regpkg können Pakete registriert werden, die mit der Microsoft. VisualStudio. Shell. dll-Assembly erstellt wurden. Es ist jedoch nicht möglich, Pakete zu registrieren, die mit neueren Versionen dieser Assembly erstellt wurden.

## <a name="see-also"></a>Siehe auch
- [VSPackages](../../extensibility/internals/vspackages.md)