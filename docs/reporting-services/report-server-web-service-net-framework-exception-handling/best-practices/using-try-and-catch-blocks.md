---
title: Try ブロックと Catch ブロックの使用 | Microsoft Docs
description: try ブロックと catch ブロックを使用して適切な例外処理を適用することによって、無効な要求に対して別の保護レイヤーを提供する方法について説明します。
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 51f6c4d3cbc7751df8e7685835057c4c5e58daa9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "80216358"
---
# <a name="using-try-and-catch-blocks"></a>Try ブロックと Catch ブロックの使用
  条件ステートメントをコードに追加し、レポート サーバーに無効な要求が発行されないようにしたら、try ブロックと catch ブロックを使用して十分な例外処理を指定してください。 これによって、レポート サーバーを無効な要求からさらに保護することができます。 レポート サーバーへの要求を try ブロックに入れ、要求が原因でレポート サーバーが例外をスローしたときは、その例外を catch ブロックでキャッチすることで、アプリケーションが異常終了するのを防ぐことができます。 例外をキャッチしたら、例外を使用して別のことを実行するようにユーザーに指示することができます。または、エラーが発生したことだけをわかりやすくユーザーに通知することもできます。 最終的には、ブロックを使用してすべてのリソースをクリーンアップできます。 try ブロックや catch ブロックの不必要な重複を避けるために、汎用的な例外処理プランを生成することが理想的です。  
  
 次の例では、try ブロックと catch ブロックを使用して例外処理コードの信頼性を高めています。  
  
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
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [Reporting Services における例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
