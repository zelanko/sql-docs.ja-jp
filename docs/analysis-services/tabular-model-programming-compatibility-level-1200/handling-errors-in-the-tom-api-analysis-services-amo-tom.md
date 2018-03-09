---
title: "TOM API (Analysis Services AMO-TOM) でのエラー処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ec44daa0-a90e-42ad-b70d-6a7a7a4e4b7b
caps.latest.revision: "4"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fe73f11bb44968e7091fe522f4905e3640c95282
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="handling-errors-in-the-tom-api-analysis-services-amo-tom"></a>TOM API (Analysis Services AMO-TOM) でのエラーを処理
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Analysis Services 管理オブジェクト (AMO) 表形式オブジェクト モデル (TOM) は、ユーザーにエラー状態を報告するためのメカニズムとして例外を使用するように、マネージ ライブラリの一般的な方法です。  

AMO TOM にエラーが検出されると、スローされることに加えていくつかの標準的な .NET 例外と同様に**ArgumentException**と**InvalidOperationException**TOM も TOM に固有のいくつかの例外をスローできます。  

TOM 例外はから派生[AmoException クラス](http://msdn.microsoft.com/library/microsoft.analysisservices.amoexception.aspx)、両方の AMO および TOM に固有の例外に対応します。 

TOM での例外処理を示すためには、見てみましょうこれより一般的な例外の 1 つ[OperationException クラス](http://msdn.microsoft.com/library/microsoft.analysisservices.operationexception.aspx)です。

**OperationException**ユーザーが Analysis Services サーバーに対する操作を開始し、アクションが法律、できなかったためか、別の内部または外部のエラーのため、操作を実行するサーバーが失敗した場合にスローされます。 

スローされると、* * * * OperationException オブジェクトがサーバーによって返される XMLA エラーの一覧に含まれます。 

サーバーが無効な変更を受け入れないことに注意してください。 この場合、元に戻す、**モデル**ツリーを使用して前回正常起動時の状態に戻す、 [UndoLocalChanges メソッド](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.model.undolocalchanges.aspx)モデルを修正してから、再実行してください、します。 

## <a name="code-example-handle-exceptions"></a>例外処理のコード例: 
 
```
 try 
 { 
  // Change the Model, for example create a table. 
  // … 
   model.saveChanges(); 
 } 
  catch(operationException ex) 
 { 
  foreach(XmlaError err in ex.Results.OfType<XmlaError>().cast<XmlaError>()) 
  { 
   Console.WriteLine(“Error returned from the server:” + err.Messsage ); 
  } 
 } 
```

## <a name="next-steps"></a>次の手順

その他の関連する例外を以下に示します。

- [TomInternalException クラス](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tominternalexception.aspx)
- [TomValidationException クラス](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.tomvalidationexception.aspx)
- [JsonSerializationException クラス](http://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_JsonSerializationException.htm)
