---
title: 'Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 319cfee254aa0b0f1709fa566e4e1bbca208eb9a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589954"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Schritt 7: Hinzufügen von Dialogfeldkomponenten zum Formular

In diesem Schritt fügen Sie Ihrem Formular die Komponenten <xref:System.Windows.Forms.OpenFileDialog> und <xref:System.Windows.Forms.ColorDialog> hinzu, damit Ihre App Bilddateien öffnen und eine Hintergrundfarbe auswählen kann.

Eine Komponente ist in gewisser Hinsicht mit einem Steuerelement vergleichbar. Zum Hinzufügen einer Komponente in Ihr Formular verwenden Sie die **Toolbox**, und Sie legen die Eigenschaften im **Eigenschaftenfenster** fest. Aber im Gegensatz zu einem Steuerelement wird dem Formular beim Hinzufügen einer Komponente kein für den Benutzer sichtbares Element hinzugefügt. Stattdessen stellt die Komponente bestimmte Verhalten bereit, die Sie mit Code auslösen können. Es handelt sich dabei um eine Komponente, die das Dialogfeld **Datei öffnen** anzeigt.

## <a name="to-add-dialog-components-to-your-form"></a>So fügen Sie dem Formular Dialogfeldkomponenten hinzu

1. Öffnen Sie den **Windows Forms-Designer** (**Form1.cs [Entwurf]** ), und öffnen Sie dann die Gruppe **Dialogfelder** in der **Toolbox**.

    > [!NOTE]
    > Die Gruppe **Dialogfelder** in der **Toolbox** verfügt über Komponenten zum Öffnen vieler nützlicher Dialogfelder, die z.B. zum Öffnen und Speichern von Dateien, Durchsuchen von Ordnern und Auswählen von Schriftarten und Farben verwendet werden können. Sie verwenden in diesem Projekt zwei Dialogfeldkomponenten: OpenFileDialog und ColorDialog.

1. Doppelklicken Sie auf **OpenFileDialog**, um dem Formular eine Komponente mit dem Namen **openFileDialog1** hinzuzufügen. Doppelklicken Sie in der **Toolbox** auf **ColorDialog**, um dem Formular eine Komponente mit dem Namen **colorDialog1** hinzuzufügen. (Sie verwenden diese Komponente im nächsten Lernprogrammschritt.) Unten im **Windows Forms-Designer** sollte ein Bereich angezeigt werden (unterhalb des Formulars **Picture Viewer**), das wie im folgenden Bild gezeigt ein Symbol für jede der beiden hinzugefügten Dialogfeldkomponenten enthält.

     ![Dialogfeldkomponenten](../ide/media/express_dialogsadded.png)<br>***Dialog****feldkomponenten*

1. Wählen Sie das Symbol **openFileDialog1** im unteren Bereich des **Windows Forms-Designers** aus. Legen Sie zwei Eigenschaften fest:

    - Legen Sie die Eigenschaft **Filter** auf Folgendes fest (Sie können den Code kopieren und einfügen):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Legen Sie für die Eigenschaft **Title** (Titel) Folgendes fest: **Select a picture file** (Bilddatei auswählen).

         Die Eigenschafteneinstellungen für **Filter** geben die Arten von Dateitypen an, die im Dateidialogfeld **Select a picture** („Bilddatei auswählen“) angezeigt werden.

    > [!TIP]
    > Öffnen Sie **Editor** oder **Paint**, und wählen Sie in der Menüleiste **Datei** > **Öffnen** aus, um ein Beispiel für das Dialogfeld **Datei öffnen** in einer anderen Anwendung zu sehen. Beachten Sie, dass neben dem Dateinamen eine Dropdownliste angezeigt wird, in der Sie den Dateityp auswählen können. <br/><br/>Sie haben soeben die **Filter**-Eigenschaft in der **OpenFileDialog**-Komponente verwendet, um diese Dropdownliste in Ihrer App einzurichten. Beachten Sie auch, dass die Eigenschaften **Title** und **Filter** im **Eigenschaftenfenster** fett sind. Hierdurch kennzeichnet die IDE alle Eigenschaften, deren Standardwerte geändert wurden.

## <a name="next-steps"></a>Nächste Schritte

* Den nächsten Schritt des Tutorials finden Sie unter **[Schritt 8: Schreiben von Code für den Ereignishandler der Schaltfläche „Bild anzeigen“](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)** .

* Den vorherigen Schritt des Tutorials finden Sie unter [Schritt 6: Benennen der Schaltflächen-Steuerelemente](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Siehe auch

* [Tutorial 2: Erstellen eines Mathequiz mit Zeitmessung](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Erstellen eines Vergleichsspiels](tutorial-3-create-a-matching-game.md)
