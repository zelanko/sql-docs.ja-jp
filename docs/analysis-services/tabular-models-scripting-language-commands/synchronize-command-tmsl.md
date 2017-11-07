---
title: "Synchronize コマンド (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a32ff053-f38f-49d7-afdc-e19f59c88135
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2904954269f32dc80d603c3c0b045685d58bc2d5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="synchronize-command-tmsl"></a>Synchronize コマンド (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later](../../includes/ssas-appliesto-sql2016-later.md)]

  Analysis Services データベースを既存の別のデータベースと同期させます。  
  
## <a name="request"></a>要求  
 JSON で受け入れられるプロパティ synchronize コマンドのとおりです。  
  
```  
{   
   "synchronize":{   
      "database":"AdventureWorksDW_Production",  
      "source":"Provider=MSOLAP.7;Data Source=localhost;Integrated Security=SSPI;Initial Catalog=AdventureWorksDW_Dev",  
      "synchronizeSecurity":"copyAll",  
      "applyCompression":true  
   }  
}  
```  
  
 JSON で受け入れられるプロパティ synchronize コマンドのとおりです。  
  
||||  
|-|-|-|  
|**プロパティ**|**[Default]**|**Description**|  
|[データベース]||同期するデータベース オブジェクトの名前。|  
|source||移行元サーバーへの接続に使用する接続文字列。|  
|synchronizeSecurity|skipMembership|ロールや権限など、セキュリティ定義を復元する方法を指定する列挙値。 有効な値には、skipMembership、copyAll、ignoresecurity のいずれかが含まれています。|  
|applyCompression|True|True の場合、圧縮、同期操作中に適用されることを示すブール値それ以外の場合は false。|  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドであらかじめ用意されているスクリプトを生成するには、データベースの同期 ダイアログ ボックスで スクリプト ボタンをクリックします。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください[表形式モデル スクリプト言語 & #40 です。TMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)明確にする新機能がサポートされている.  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

