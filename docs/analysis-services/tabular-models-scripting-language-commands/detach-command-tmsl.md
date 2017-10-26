---
title: "Detach コマンド (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 413b49cb-ea8f-415c-a059-ce692b7771a1
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dfa0440270971b80d6cd1f6789534cedb6f976ad
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="detach-command-tmsl"></a>Detach コマンド (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  サーバーから Analysis Services データベースをデタッチします。  
  
## <a name="request"></a>要求  
  
```  
{   
   "detach": {    
      "database":"AdventureWorksDW2014",  
      "password": "secret"  
   }  
}  
```  
  
 JSON で受け入れられるプロパティ detach コマンドは次のようにします。  
  
||||  
|-|-|-|  
|**プロパティ**|**[Default]**|**Description**|  
|[データベース]|[必須]|デタッチするデータベース オブジェクトの名前。|  
|パスワード|空|デタッチされたデータベースで機密データの暗号化に使用するパスワード。|  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドであらかじめ用意されているスクリプトを生成するには、[デタッチ] ダイアログ ボックスの [スクリプト] ボタンをクリックします。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください ([表形式モデル スクリプト言語 & #40 です。TMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) がサポートされているものより明確にします。  

## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Analysis Services データベースのインポートとデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)  
  
  

