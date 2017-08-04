---
title: "スクリプト タスクによるインストールされたプリンターを検索しています |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 1de1fae5c30648eba7cb62840ef3ff9f9aac13f9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="finding-installed-printers-with-the-script-task"></a>スクリプト タスクによるインストールされたプリンターの検索
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで変換されたデータは、最後の変換先で印刷レポートになることがよくあります。 **System.Drawing.Printing**で名前空間、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]プリンターを操作するためのクラスを提供します。  
  
> [!NOTE]  
>  複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。 詳細については、「 [カスタム タスクの開発](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。  
  
## <a name="description"></a>Description  
 次の例では、米国で使用されているリーガル サイズの用紙をサポートしているプリンターがサーバーにインストールされている場合、そのプリンターを検索します。 サポートされる用紙サイズを調べるコードは、private 関数にカプセル化されています。 各プリンターの設定を確認する間にスクリプトの進行状況を追跡できるように、スクリプトでは <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを使用して、リーガル サイズ用紙をサポートするプリンターには情報メッセージを出力し、リーガル サイズ用紙をサポートしないプリンターには警告メッセージを出力します。 これらのメッセージが表示される、**出力**のウィンドウ、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE、デザイナーでパッケージを実行するとします。  
  
#### <a name="to-configure-this-script-task-example"></a>このスクリプト タスクの例を構成するには  
  
1.  という名前の変数を作成する`PrinterList`型**オブジェクト**です。  
  
2.  **スクリプト**のページ、**スクリプト タスク エディター**、ReadWriteVariables プロパティにこの変数を追加します。  
  
3.  スクリプト プロジェクトに参照を追加、 **System.Drawing**名前空間。  
  
4.  コードを使用して**Imports**をインポートするステートメント、 **System.Collections**と**System.Drawing.Printing**名前空間。  
  
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
  
## <a name="see-also"></a>参照  
 [スクリプト タスクの例](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
