---
title: "スクリプト タスクによる画像の操作 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- graphics [Integration Services]
- Script task [Integration Services], images
- Drawing namespace
- images [Integration Services]
- SSIS Script task, images
- Script task [Integration Services], examples
- thumbnails [Integration Services]
- System.Drawing namespace
- JPEG format [Integration Services]
- .jpeg files
ms.assetid: 74aeb7ab-51b2-4b9f-84ee-0b46a7908ab9
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4a28fe7c6024d8cf5669199e5f33e3532013e4d3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-images-with-the-script-task"></a>スクリプト タスクによる画像の操作
  製品またはユーザーのデータベースには、テキストや数値データに加え、画像も頻繁に含まれています。 **System.Drawing** Microsoft .NET Framework の名前空間がイメージを操作するためのクラスを提供します。  
  
 [例 1: 画像を JPEG 形式に変換します。](#example1)  
  
 [例 2: を作成し、サムネイル画像を保存](#example2)  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
##  <a name="example1"></a>例 1 の説明: 画像を JPEG 形式に変換します。  
 次の例では、変数で指定された画像ファイルを開き、エンコーダーを使用して圧縮 JPEG ファイルとして保存します。 エンコーダー情報を取得するコードは、private 関数にカプセル化されています。  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a>このスクリプト タスクの例を単一の画像ファイルで使用するように構成するには  
  
1.  `CurrentImageFile` という名前の文字列変数を作成し、その値を既存の画像ファイルのパスおよびファイル名に設定します。  
  
2.  **スクリプト**のページ、**スクリプト タスク エディター**、追加、`CurrentImageFile`変数を**ReadOnlyVariables**プロパティです。  
  
3.  スクリプト プロジェクトに参照を設定、 **System.Drawing**名前空間。  
  
4.  コードで使用**Imports**をインポートするステートメント、 **System.Drawing**と**System.IO**名前空間。  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a>このスクリプト タスクの例を複数の画像ファイルで使用するように構成するには  
  
1.  Foreach ループ コンテナー内にスクリプト タスクを入れます。  
  
2.  **コレクション**のページ、 **Foreach ループ エディター**を選択、 **Foreach File 列挙子**列挙子としてソースのパスおよびファイル マスクを指定してなどのファイル"*.bmp"として  
  
3.  **変数のマッピング**ページで、マップ、`CurrentImageFile`変数をインデックス 0 にします。 この変数は、列挙子が繰り返されるたびに、現在のファイル名をスクリプト タスクに渡します。  
  
    > [!NOTE]  
    >  この手順は、単一の画像ファイルで使用する場合の手順としてリストされているものに追加されます。  
  
### <a name="example-1-code"></a>コード例 1  
  
```vb  
Public Sub Main()  
  
    'Create and initialize variables.  
    Dim currentFile As String  
    Dim newFile As String  
    Dim bmp As Bitmap  
    Dim eps As New Imaging.EncoderParameters(1)  
    Dim ici As Imaging.ImageCodecInfo  
    Dim supportedExtensions() As String = _  
        {".BMP", ".GIF", ".JPG", ".JPEG", ".EXIF", ".PNG", _  
        ".TIFF", ".TIF", ".ICO", ".ICON"}  
  
    Try  
        'Store the variable in a string for local manipulation.  
        currentFile = Dts.Variables("CurrentImageFile").Value.ToString  
        'Check the extension of the file against a list of  
        'files that the Bitmap class supports.  
        If Array.IndexOf(supportedExtensions, _  
            Path.GetExtension(currentFile).ToUpper) > -1 Then  
  
            'Load the file.  
            bmp = New Bitmap(currentFile)  
  
            'Calculate the new name for the compressed image.  
            'Note: This will overwrite existing JPEGs.  
            newFile = Path.Combine( _  
                Path.GetDirectoryName(currentFile), _  
                String.Concat(Path.GetFileNameWithoutExtension(currentFile), _  
                ".jpg"))  
  
            'Specify the compression ratio (0=worst quality, 100=best quality).  
            eps.Param(0) = New Imaging.EncoderParameter( _  
                Imaging.Encoder.Quality, 75)  
  
            'Retrieve the ImageCodecInfo associated with the jpeg format.  
            ici = GetEncoderInfo("image/jpeg")  
  
            'Save the file, compressing it into the jpeg encoding.  
            bmp.Save(newFile, ici, eps)  
        Else  
            'The file is not supported by the Bitmap class.  
            Dts.Events.FireWarning(0, "Image Resampling Sample", _  
                "File " & currentFile & " is not a supported format.", _  
                "", 0)  
         End If  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Image Resampling Sample", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Function GetEncoderInfo(ByVal mimeType As String) As Imaging.ImageCodecInfo  
  
    'The available image codecs are returned as an array,  
    'which requires code to iterate until the specified codec is found.  
  
    Dim count As Integer  
    Dim encoders() As Imaging.ImageCodecInfo  
  
    encoders = Imaging.ImageCodecInfo.GetImageEncoders()  
  
    For count = 0 To encoders.Length  
        If encoders(count).MimeType = mimeType Then  
            Return encoders(count)  
        End If  
    Next  
  
    'This point is only reached if a codec is not found.  
    Err.Raise(513, "Image Resampling Sample", String.Format( _  
        "The {0} codec is not available. Unable to compress file.", _  
            mimeType))  
    Return Nothing  
  
End Function  
  
```  
  
##  <a name="example2"></a>例 2 の説明: を作成し、サムネイル画像を保存  
 次の例では、変数で指定された画像ファイルを開いて、一定の縦横比を維持しながら画像のサムネイルを作成し、ファイル名を変更してサムネイルを保存します。 一定の縦横比を維持しながらサムネイルの高さと幅を計算するコードは、private サブルーチンでカプセル化されています。  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a>このスクリプト タスクの例を単一の画像ファイルで使用するように構成するには  
  
1.  `CurrentImageFile` という名前の文字列変数を作成し、その値を既存の画像ファイルのパスおよびファイル名に設定します。  
  
2.  次に `MaxThumbSize` 整数変数を作成し、100 などのピクセル値を割り当てます。  
  
3.  **スクリプト**のページ、**スクリプト タスク エディター**、両方の変数を追加して、 **ReadOnlyVariables**プロパティです。  
  
4.  スクリプト プロジェクトに参照を設定、 **System.Drawing**名前空間。  
  
5.  コードで使用**Imports**をインポートするステートメント、 **System.Drawing**と**System.IO**名前空間。  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a>このスクリプト タスクの例を複数の画像ファイルで使用するように構成するには  
  
1.  Foreach ループ コンテナー内にスクリプト タスクを入れます。  
  
2.  **コレクション**のページ、 **Foreach ループ エディター**、select、 **Foreach File 列挙子**として、**列挙子**を指定し、"*.jpg"などのソース ファイルのパスおよびファイル マスク  
  
3.  **変数のマッピング**ページで、マップ、`CurrentImageFile`変数をインデックス 0 にします。 この変数は、列挙子が繰り返されるたびに、現在のファイル名をスクリプト タスクに渡します。  
  
    > [!NOTE]  
    >  この手順は、単一の画像ファイルで使用する場合の手順としてリストされているものに追加されます。  
  
### <a name="example-2-code"></a>コード例 2  
  
```vb  
Public Sub Main()  
  
    Dim currentImageFile As String  
    Dim currentImage As Image  
    Dim maxThumbSize As Integer  
    Dim thumbnailImage As Image  
    Dim thumbnailFile As String  
    Dim thumbnailHeight As Integer  
    Dim thumbnailWidth As Integer  
  
    currentImageFile = Dts.Variables("CurrentImageFile").Value.ToString  
    thumbnailFile = Path.Combine( _  
        Path.GetDirectoryName(currentImageFile), _  
        String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), _  
        "_thumbnail.jpg"))  
  
    Try  
        currentImage = Image.FromFile(currentImageFile)  
  
        maxThumbSize = CType(Dts.Variables("MaxThumbSize").Value, Integer)  
        CalculateThumbnailSize( _  
            maxThumbSize, currentImage, thumbnailWidth, thumbnailHeight)  
  
        thumbnailImage = currentImage.GetThumbnailImage( _  
           thumbnailWidth, thumbnailHeight, Nothing, Nothing)  
        thumbnailImage.Save(thumbnailFile)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, "Script Task Example", _  
        ex.Message & ControlChars.CrLf & ex.StackTrace, _  
        String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Sub CalculateThumbnailSize( _  
    ByVal maxSize As Integer, ByVal sourceImage As Image, _  
    ByRef thumbWidth As Integer, ByRef thumbHeight As Integer)  
  
    If sourceImage.Width > sourceImage.Height Then  
        thumbWidth = maxSize  
        thumbHeight = CInt((maxSize / sourceImage.Width) * sourceImage.Height)  
    Else  
        thumbHeight = maxSize  
        thumbWidth = CInt((maxSize / sourceImage.Height) * sourceImage.Width)  
    End If  
  
End Sub  
```  
  
```csharp  
bool ThumbnailCallback()  
        {  
            return false;  
        }  
        public void Main()  
        {  
  
            string currentImageFile;  
            Image currentImage;  
            int maxThumbSize;  
            Image thumbnailImage;  
            string thumbnailFile;  
            int thumbnailHeight = 0;  
            int thumbnailWidth = 0;  
  
            currentImageFile = Dts.Variables["CurrentImageFile"].Value.ToString();  
            thumbnailFile = Path.Combine(Path.GetDirectoryName(currentImageFile), String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), "_thumbnail.jpg"));  
  
            try  
            {  
  
                currentImage = Image.FromFile(currentImageFile);  
  
                maxThumbSize = (int)Dts.Variables["MaxThumbSize"].Value;  
                CalculateThumbnailSize(maxThumbSize, currentImage, ref thumbnailWidth, ref thumbnailHeight);  
  
                Image.GetThumbnailImageAbort myCallback = new Image.GetThumbnailImageAbort(ThumbnailCallback);  
  
                thumbnailImage = currentImage.GetThumbnailImage(thumbnailWidth, thumbnailHeight, ThumbnailCallback, IntPtr.Zero);  
                thumbnailImage.Save(thumbnailFile);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
  
        private void CalculateThumbnailSize(int maxSize, Image sourceImage, ref int thumbWidth, ref int thumbHeight)  
        {  
  
            if (sourceImage.Width > sourceImage.Height)  
            {  
                thumbWidth = maxSize;  
                thumbHeight = (int)(sourceImage.Height * maxSize / sourceImage.Width);  
            }  
            else  
            {  
                thumbHeight = maxSize;  
                thumbWidth = (int)(sourceImage.Width * maxSize / sourceImage.Height);  
  
            }  
  
        }  
  
```  
  
  
