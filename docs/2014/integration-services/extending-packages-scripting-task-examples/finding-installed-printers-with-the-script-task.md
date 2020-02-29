---
title: スクリプト タスクによるインストールされたプリンターの検索 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 956a73f76e113eb0a50f628150e47ed33791cc97
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176241"
---
# <a name="finding-installed-printers-with-the-script-task"></a>スクリプト タスクによるインストールされたプリンターの検索
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで変換されたデータは、最後の変換先で印刷レポートになることがよくあります。 [!INCLUDE[msCoName](../../includes/msconame-md.md)]の`System.Drawing.Printing` [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]名前空間は、プリンターを操作するためのクラスを提供します。

> [!NOTE]
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。

## <a name="description"></a>説明
 次の例では、米国で使用されているリーガル サイズの用紙をサポートしているプリンターがサーバーにインストールされている場合、そのプリンターを検索します。 サポートされる用紙サイズを調べるコードは、private 関数にカプセル化されています。 各プリンターの設定を確認する間にスクリプトの進行状況を追跡できるように、スクリプトでは <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを使用して、リーガル サイズ用紙をサポートするプリンターには情報メッセージを出力し、リーガル サイズ用紙をサポートしないプリンターには警告メッセージを出力します。 デザイナーでパッケージを実行すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE の **[出力]** ウィンドウにこれらのメッセージが表示されます。

#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには

1.  
  `PrinterList` という名前の、`Object` 型の変数を作成します。

2.  **[スクリプト タスク エディター]** の **[スクリプト]** ページで、ReadWriteVariables プロパティに追加します。

3.  このスクリプト プロジェクトでは、参照を **System.Drawing** 名前空間に追加します。

4.  コードでは、ステートメント`Imports`を使用して、**システムコレクション**と`System.Drawing.Printing`名前空間をインポートします。

### <a name="code"></a>コード

```vb
Public Sub Main()

    Dim printerName As String
    Dim currentPrinter As New PrinterSettings
    Dim size As PaperSize

    Dim printerList As New ArrayList
    For Each printerName In PrinterSettings.InstalledPrinters
        currentPrinter.PrinterName = printerName
        If PrinterHasLegalPaper(currentPrinter) Then
            printerList.Add(printerName)
            Dts.Events.FireInformation(0, "Example", _
                "Printer " & printerName & " has legal paper.", _
                String.Empty, 0, False)
        Else
            Dts.Events.FireWarning(0, "Example", _
                "Printer " & printerName & " DOES NOT have legal paper.", _
                String.Empty, 0)
        End If
    Next

    Dts.Variables("PrinterList").Value = printerList

    Dts.TaskResult = ScriptResults.Success

End Sub

Private Function PrinterHasLegalPaper( _
    ByVal thisPrinter As PrinterSettings) As Boolean

    Dim size As PaperSize
    Dim hasLegal As Boolean = False

    For Each size In thisPrinter.PaperSizes
        If size.Kind = PaperKind.Legal Then
            hasLegal = True
        End If
    Next

    Return hasLegal

End Function
```

```csharp
public void Main()
        {

            PrinterSettings currentPrinter = new PrinterSettings();
            PaperSize size;
            Boolean Flag = false;

            ArrayList printerList = new ArrayList();
            foreach (string printerName in PrinterSettings.InstalledPrinters)
            {
                currentPrinter.PrinterName = printerName;
                if (PrinterHasLegalPaper(currentPrinter))
                {
                    printerList.Add(printerName);
                    Dts.Events.FireInformation(0, "Example", "Printer " + printerName + " has legal paper.", String.Empty, 0, ref Flag);
                }
                else
                {
                    Dts.Events.FireWarning(0, "Example", "Printer " + printerName + " DOES NOT have legal paper.", String.Empty, 0);
                }
            }

            Dts.Variables["PrinterList"].Value = printerList;

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private bool PrinterHasLegalPaper(PrinterSettings thisPrinter)
        {

            bool hasLegal = false;

            foreach (PaperSize size in thisPrinter.PaperSizes)
            {
                if (size.Kind == PaperKind.Legal)
                {
                    hasLegal = true;
                }
            }

            return hasLegal;

        }
```

![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services に関するページを参照してください。](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。

## <a name="see-also"></a>参照
 [スクリプト タスクの例](../extending-packages-scripting-task-examples/script-task-examples.md)


