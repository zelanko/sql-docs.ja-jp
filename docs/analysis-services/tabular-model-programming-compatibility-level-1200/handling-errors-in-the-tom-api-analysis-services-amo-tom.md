---
title: "TOM API (Analysis Services AMO-TOM) でのエラー処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ec44daa0-a90e-42ad-b70d-6a7a7a4e4b7b
caps.latest.revision: 4
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ab72f854e36aeaa9bd0ea64ede645cbadffc018
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="handling-errors-in-the-tom-api-analysis-services-amo-tom"></a>TOM API (Analysis Services AMO-TOM) でのエラーを処理

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

Analysis Services 管理オブジェクト (AMO) 表形式オブジェクト モデル (TOM) は、ユーザーにエラー状態を報告するためのメカニズムとして例外を使用するように、マネージ ライブラリの一般的な方法です。  

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

