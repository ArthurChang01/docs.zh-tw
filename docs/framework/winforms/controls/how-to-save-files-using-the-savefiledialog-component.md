---
title: 如何：使用 SaveFileDialog 元件儲存檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: 32de7f7e38195271e179d4fae3884b7a39f37c45
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868079"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>如何：使用 SaveFileDialog 元件儲存檔案

<xref:System.Windows.Forms.SaveFileDialog> 元件可讓使用者流覽檔案系統，並選取要儲存的檔案。 對話方塊會傳回使用者在對話方塊中所選取之檔案的路徑和名稱。 不過，您必須撰寫程式碼，以實際將檔案寫入至磁碟。

### <a name="to-save-a-file-using-the-savefiledialog-component"></a>使用 SaveFileDialog 元件儲存檔案

- 顯示 [儲存檔案] 對話方塊，並呼叫方法來儲存使用者所選取的檔案。

  使用 <xref:System.Windows.Forms.SaveFileDialog> 元件的 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法來儲存檔案。 這個方法會提供您可以寫入的 <xref:System.IO.Stream> 物件。

  下列範例會使用 <xref:System.Windows.Forms.DialogResult> 屬性來取得檔案的名稱，以及用來儲存檔案的 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法。 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法可提供您將檔案寫入的資料流程。

  在下列範例中，有一個 <xref:System.Windows.Forms.Button> 控制項已指派映射。 當您按一下此按鈕時，<xref:System.Windows.Forms.SaveFileDialog> 元件會具現化，並具有允許 .gif、jpeg 和 .bmp 類型檔案的篩選準則。 如果在 [儲存檔案] 對話方塊中選取這類型的檔案，則會儲存按鈕的影像。

  > [!IMPORTANT]
  > 若要取得或設定 <xref:System.Windows.Forms.FileDialog.FileName%2A> 屬性，您的元件需要由 <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> 類別授與的許可權層級。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱 [Code Access Security Basics](../../misc/code-access-security-basics.md)。

  此範例假設您的表單具有 <xref:System.Windows.Forms.Button> 控制項，其 <xref:System.Windows.Forms.ButtonBase.Image%2A> 屬性設定為 .gif、jpeg 或 .bmp 類型的檔案。

  > [!NOTE]
  > <xref:System.Windows.Forms.FileDialog> 類別的 <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> 屬性（由於繼承，這是 <xref:System.Windows.Forms.SaveFileDialog> 類別的一部分）使用以一為基礎的索引。 如果您要撰寫程式碼，以特定格式來儲存資料 (例如，以純文字與二進位格式儲存檔案)，則這十分重要。 下列範例具有這個屬性。

  ```vb
  Private Sub Button2_Click(ByVal sender As System.Object, _
  ByVal e As System.EventArgs) Handles Button2.Click
      ' Displays a SaveFileDialog so the user can save the Image
      ' assigned to Button2.
      Dim saveFileDialog1 As New SaveFileDialog()
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"
      saveFileDialog1.Title = "Save an Image File"
      saveFileDialog1.ShowDialog()

      ' If the file name is not an empty string open it for saving.
      If saveFileDialog1.FileName <> "" Then
        ' Saves the Image via a FileStream created by the OpenFile method.
        Dim fs As System.IO.FileStream = Ctype _
            (saveFileDialog1.OpenFile(), System.IO.FileStream)
        ' Saves the Image in the appropriate ImageFormat based upon the
        ' file type selected in the dialog box.
        ' NOTE that the FilterIndex property is one-based.
        Select Case saveFileDialog1.FilterIndex
            Case 1
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Jpeg)

            Case 2
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Bmp)

            Case 3
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Gif)
          End Select

          fs.Close()
      End If
  End Sub
  ```

  ```csharp
  private void button2_Click(object sender, System.EventArgs e)
  {
      // Displays a SaveFileDialog so the user can save the Image
      // assigned to Button2.
      SaveFileDialog saveFileDialog1 = new SaveFileDialog();
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
      saveFileDialog1.Title = "Save an Image File";
      saveFileDialog1.ShowDialog();

      // If the file name is not an empty string open it for saving.
      if(saveFileDialog1.FileName != "")
      {
        // Saves the Image via a FileStream created by the OpenFile method.
        System.IO.FileStream fs =
            (System.IO.FileStream)saveFileDialog1.OpenFile();
        // Saves the Image in the appropriate ImageFormat based upon the
        // File type selected in the dialog box.
        // NOTE that the FilterIndex property is one-based.
        switch(saveFileDialog1.FilterIndex)
        {
            case 1 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Jpeg);
            break;

            case 2 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Bmp);
            break;

            case 3 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Gif);
            break;
        }

      fs.Close();
      }
  }
  ```

  ```cpp
  private:
      System::Void button2_Click(System::Object ^ sender,
        System::EventArgs ^ e)
      {
        // Displays a SaveFileDialog so the user can save the Image
        // assigned to Button2.
        SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();
        saveFileDialog1->Filter =
            "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
        saveFileDialog1->Title = "Save an Image File";
        saveFileDialog1->ShowDialog();
        // If the file name is not an empty string, open it for saving.
        if(saveFileDialog1->FileName != "")
        {
            // Saves the Image through a FileStream created by
            // the OpenFile method.
            System::IO::FileStream ^ fs =
              safe_cast\<System::IO::FileStream*>(
              saveFileDialog1->OpenFile());
            // Saves the Image in the appropriate ImageFormat based on
            // the file type selected in the dialog box.
            // Note that the FilterIndex property is one based.
            switch(saveFileDialog1->FilterIndex)
            {
              case 1 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Jpeg);
                  break;
              case 2 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Bmp);
                  break;
              case 3 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Gif);
                  break;
            }
        fs->Close();
        }
      }
  ```

  （視覺C#效果和C++視覺效果）將下列程式碼放在表單的函式中，以註冊事件處理常式。

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  如需有關寫入檔案資料流程的詳細資訊，請參閱 <xref:System.IO.FileStream.BeginWrite%2A> 和 <xref:System.IO.FileStream.Write%2A>。

  > [!NOTE]
  > 某些控制項（例如 <xref:System.Windows.Forms.RichTextBox> 控制項）具有儲存檔案的能力。

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog 元件](savefiledialog-component-windows-forms.md)
