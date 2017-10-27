---
title: "無効な要求を防止 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 830e388abe098bab402e5af56486d1e6cd528e98
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="preventing-invalid-requests"></a>無効な要求の回避
  アプリケーション フローを分析し、レポート サーバーに送信される要求が有効であることを確認することによって、ある種類の例外がスローされないようにすることができます。 たとえば、ユーザーがレポートの名前、データ ソース、その他のレポート サーバー アイテムを追加または更新できるアプリケーションで、ユーザーが入力するテキストを検証する必要があります。 また、要求をレポート サーバーに送信する前に予約文字を常に確認する必要があります。 使用条件**場合**ステートメントまたはレポート サーバーに要求を送信するために必要な条件を満たしていないことをユーザーにアラートを生成する、コード内の他の論理コンストラクト。  
  
 次の単純な C# の例では、ユーザーがスラッシュ (/) 文字を含む名前でレポートを作成しようとすると、わかりやすいエラー メッセージが表示されます。  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 要求がレポート サーバーに送信する前に回避できるエラーの種類の詳細については、次を参照してください。 [SoapException エラー テーブル](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)です。 Try ブロックと catch ブロックを使用して、前の例をさらに強化する方法の詳細については、次を参照してください。[再試行を使用すると、Catch ブロック](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)です。  
  
## <a name="see-also"></a>参照  
 [Reporting Services での例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  

