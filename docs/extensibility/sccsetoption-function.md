---
title: Sccsetoption-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccSetOption
helpviewer_keywords:
- SccSetOption function
ms.assetid: 4b5e6666-c24c-438a-a9df-9c52f58f8175
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f48cb84a64c036b373308dfe29bfaf5d2e028b91
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720555"
---
# <a name="sccsetoption-function"></a>SccSetOption-Funktion
Diese Funktion legt Optionen fest, mit denen das Verhalten des Quellcodeverwaltungs-Plug-ins gesteuert wird.

## <a name="syntax"></a>Syntax

```cpp
SCCRTN SccSetOption(
   LPVOID pvContext,
   LONG   nOption,
   LONG   dwVal
);
```

#### <a name="parameters"></a>Parameter
 pvcontext

in Die Kontext Struktur der Quellcodeverwaltungs-Plug-in.

 noption

in Die Option, die festgelegt wird.

 dwval Datentyp

in Einstellungen für die Option.

## <a name="return-value"></a>Rückgabewert
 Es wird erwartet, dass die Plug-in-Implementierung der Quell Code Verwaltung diese Funktion einen der folgenden Werte zurückgibt:

|Wert|Beschreibung|
|-----------|-----------------|
|SCC_OK|Die Option wurde erfolgreich festgelegt.|
|SCC_I_SHARESUBPROJOK|Wird zurückgegeben, wenn `nOption` `SCC_OPT_SHARESUBPROJ` wurde, und das Quellcodeverwaltungs-Plug-in ermöglicht der IDE, den Zielordner festzulegen.|
|SCC_E_OPNOTSUPPORTED|Die Option wurde nicht festgelegt und sollte nicht verlassen werden.|

## <a name="remarks"></a>Hinweise
 Die IDE ruft diese Funktion auf, um das Verhalten des Quellcodeverwaltungs-Plug-ins zu steuern. Der erste Parameter (`nOption`) gibt den Wert an, der festgelegt wird, während der zweite, `dwVal`, angibt, was mit diesem Wert zu tun ist. Das Plug-in speichert diese Informationen, die mit einem `pvContext``,` verknüpft sind, sodass die IDE diese Funktion nach dem Aufruf von [sccinitialize](../extensibility/sccinitialize-function.md) aufrufen muss (aber nicht unbedingt nach jedem Aufruf von [sccopenproject](../extensibility/sccopenproject-function.md)).

 Zusammenfassung der Optionen und ihrer Werte:

|`nOption`|`dwValue`|Beschreibung|
|---------------|---------------|-----------------|
|`SCC_OPT_EVENTQUEUE`|`SCC_OPT_EQ_DISABLE`<br /><br /> `SCC_OPT_EQ_ENABLE`|Aktiviert/deaktiviert hintergrundereignisqueuing.|
|`SCC_OPT_USERDATA`|Beliebiger Wert|Gibt einen Benutzer Wert an, der an die [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) -Rückruffunktion übermittelt werden soll.|
|`SCC_OPT_HASCANCELMODE`|`SCC_OPT_HCM_NO`<br /><br /> `SCC_OPT_HCM_YES`|Gibt an, ob die IDE derzeit das Abbrechen eines Vorgangs unterstützt.|
|`SCC_OPT_NAMECHANGEPFN`|Zeiger auf die [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) -Rückruffunktion|Legt einen Zeiger auf eine namens Änderungs Rückruffunktion fest.|
|`SCC_OPT_SCCCHECKOUTONLY`|`SCC_OPT_SCO_NO`<br /><br /> `SCC_OPT_SCO_YES`|Gibt an, ob die IDE das Auschecken der Dateien (über die Benutzeroberfläche der Quell Code Verwaltung) oder das Auschecken der Dateien nur über das Quellcodeverwaltungs-Plug-in zulässt.|
|`SCC_OPT_SHARESUBPROJ`|Nicht zutreffend|Wenn das Quellcodeverwaltungs-Plug-in der IDE ermöglicht, den lokalen Projektordner anzugeben, gibt das Plug-in `SCC_I_SHARESUBPROJOK` zurück.|

## <a name="scc_opt_eventqueue"></a>SCC_OPT_EVENTQUEUE
 Wenn `nOption` `SCC_OPT_EVENTQUEUE` ist, wird die Hintergrundverarbeitung durch die IDE deaktiviert (oder erneut aktiviert). Beispielsweise weist die IDE während einer Kompilierung möglicherweise das Quellcodeverwaltungs-Plug-in an, die Verarbeitung jeglicher Art zu verhindern. Nach der Kompilierung wird die Hintergrundverarbeitung erneut aktiviert, um die Ereignis Warteschlange des Plug-Ins auf dem neuesten Stand zu halten. Entsprechend dem `SCC_OPT_EVENTQUEUE` Wert `nOption` gibt es zwei mögliche Werte für `dwVal`, nämlich `SCC_OPT_EQ_ENABLE` und `SCC_OPT_EQ_DISABLE`.

## <a name="scc_opt_hascancelmode"></a>SCC_OPT_HASCANCELMODE
 Wenn der Wert für `nOption` `SCC_OPT_HASCANCELMODE` ist, können Benutzer mit der IDE lange Vorgänge abbrechen. Wenn Sie `dwVal` auf `SCC_OPT_HCM_NO` festlegen (Standardeinstellung), wird angegeben, dass die IDE keinen Abbruch Modus aufweist. Das Quellcodeverwaltungs-Plug-in muss seine eigene Schaltfläche Abbrechen anbieten, wenn der Benutzer in der Lage sein soll, abzubrechen. `SCC_OPT_HCM_YES` gibt an, dass die IDE die Möglichkeit bietet, einen Vorgang abzubrechen, sodass das SCC-Plug-in keine eigene Schaltfläche "Abbrechen" anzeigen muss. Wenn die IDE `dwVal` auf `SCC_OPT_HCM_YES` festlegt, ist Sie darauf vorbereitet, auf `SCC_MSG_STATUS` und `DOCANCEL` an die `lpTextOutProc` Rückruffunktion gesendeten Nachrichten zu reagieren (siehe [lptextoutproc](../extensibility/lptextoutproc.md)). Wenn die IDE diese Variable nicht festgelegt, sollte das Plug-in diese beiden Nachrichten nicht senden.

## <a name="scc_opt_namechangepfn"></a>SCC_OPT_NAMECHANGEPFN
 Wenn noption auf `SCC_OPT_NAMECHANGEPFN` festgelegt ist und das Quellcodeverwaltungs-Plug-in und die IDE dies zulassen, kann das Plug-in eine Datei in einem Quell Code Verwaltungsvorgang tatsächlich umbenennen oder verschieben. Der `dwVal` wird auf einen Funktionszeiger vom Typ [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)festgelegt. Während eines Quell Code Verwaltungs Vorgangs kann das Plug-in diese Funktion abrufen und dabei drei Parameter übergeben. Dabei handelt es sich um den alten Namen (mit dem voll qualifizierten Pfad) einer Datei, den neuen Namen (mit dem voll qualifizierten Pfad) dieser Datei und einen Zeiger auf Informationen, die für die IDE relevant sind. Die IDE sendet in diesem letzten Zeiger `SccSetOption`, wobei `nOption` auf `SCC_OPT_USERDATA` festgelegt ist, wobei `dwVal` auf die Daten zeigt. Die Unterstützung für diese Funktion ist optional. Ein vssci-Plug-in, das diese Funktion verwendet, muss seine Funktionszeiger-und Benutzerdaten Variablen zu `NULL` initialisieren, und es darf keine Rename-Funktion aufgerufen werden, es sei denn, es wurde eines angegeben. Außerdem sollte Sie darauf vorbereitet sein, den Wert zu speichern, den Sie erhalten hat, oder Sie als Reaktion auf einen neuen `SccSetOption` aufzurufen. Dies tritt nicht in der Mitte eines Quell Code Verwaltungs Befehls Vorgangs auf, kann jedoch zwischen Befehlen auftreten.

## <a name="scc_opt_scccheckoutonly"></a>SCC_OPT_SCCCHECKOUTONLY
 Wenn noption auf `SCC_OPT_SCCCHECKOUTONLY` festgelegt ist, zeigt die IDE an, dass die Dateien im aktuell geöffneten Projekt nie manuell über die Benutzeroberfläche des Quell Code Verwaltungssystems ausgecheckt werden sollen. Stattdessen sollten die Dateien nur über das Quellcodeverwaltungs-Plug-in unter IDE-Steuerelement ausgecheckt werden. Wenn `dwValue` auf `SCC_OPT_SCO_NO` festgelegt ist, bedeutet dies, dass die Dateien vom Plug-in normal behandelt werden und über die Benutzeroberfläche der Quell Code Verwaltung ausgecheckt werden können. Wenn `dwValue` auf `SCC_OPT_SCO_YES` festgelegt ist, darf nur das Plug-in Dateien Auschecken, und die Benutzeroberfläche des Quell Code Verwaltungssystems sollte nicht aufgerufen werden. Dies gilt für Situationen, in denen die IDE möglicherweise "Pseudo Dateien" hat, die für das Auschecken nur über die IDE sinnvoll sind.

## <a name="scc_opt_sharesubproj"></a>SCC_OPT_SHARESUBPROJ
 Wenn `nOption` auf `SCC_OPT_SHARESUBPROJ` festgelegt ist, testet die IDE, ob das Quellcodeverwaltungs-Plug-in beim Hinzufügen von Dateien aus der Quell Code Verwaltung einen angegebenen lokalen Ordner verwenden kann. Der Wert des `dwVal`-Parameters ist in diesem Fall nicht von Bedeutung. Wenn das Plug-in der IDE ermöglicht, den lokalen Zielordner anzugeben, in dem die Dateien aus der Quell Code Verwaltung hinzugefügt werden, wenn [sccaddfromscc](../extensibility/sccaddfromscc-function.md) aufgerufen wird, muss das Plug-in `SCC_I_SHARESUBPROJOK` zurückgeben, wenn die `SccSetOption`-Funktion aufgerufen wird. Die IDE verwendet dann den `lplpFileNames`-Parameter der `SccAddFromScc`-Funktion, um den Zielordner zu übergeben. Das Plug-in verwendet diesen Zielordner, um die aus der Quell Code Verwaltung hinzugefügten Dateien zu platzieren. Wenn das Plug-in keine `SCC_I_SHARESUBPROJOK` zurückgibt, wenn die `SCC_OPT_SHARESUBPROJ`-Option festgelegt ist, geht die IDE davon aus, dass das Plug-in nur Dateien im aktuellen lokalen Ordner hinzufügen kann.

## <a name="see-also"></a>Siehe auch
- [API-Funktionen von Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccAddFromScc](../extensibility/sccaddfromscc-function.md)
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)