---
title: Synchronize コマンド (TMSL) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4265e6fa1e2214fae53cacdb084e152005eb3647
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38033275"
---
# <a name="synchronize-command-tmsl"></a>Synchronize コマンド (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  Analysis Services データベースを既存の別のデータベースと同期させます。  
  
## <a name="request"></a>要求  
 Synchronize コマンドの JSON で受け入れられるプロパティは次のようにします。  
  
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
  
 Synchronize コマンドの JSON で受け入れられるプロパティは次のようにします。  
  
||||  
|-|-|-|  
|**プロパティ**|**[Default]**|**[説明]**|  
|[データベース]||同期するデータベース オブジェクトの名前。|  
|source||移行元サーバーへの接続に使用する接続文字列。|  
|synchronizeSecurity|skipMembership|ロールとアクセス許可を含む、セキュリティ定義を復元する方法を指定する列挙値。 有効な値には、skipMembership、ignoreSecurity、copyAll が含まれています。|  
|applyCompression|True|ブール値が true の場合、同期操作中に圧縮が適用されることを示します。それ以外の場合は false。|  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA の例外が返されます。  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンド要素は、ステートメントで使用、[メソッドの実行&#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md)次の方法で公開される、XMLA エンドポイント経由での呼び出し。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブに入力として  
  
 SSMS からこのコマンドの既製スクリプトを生成するには、データベースの同期 ダイアログ ボックスで スクリプト ボタンをクリックします。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services 表形式・ (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855)セクション 3.1.5.2.2 JSON 表形式メタデータ コマンドとオブジェクトの構造を記述するがドキュメントに含まれています。 現時点では、そのドキュメントは、コマンドと TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください[Tabular Model Scripting Language &#40;TMSL&#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)clarification on でサポートされている機能の  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
