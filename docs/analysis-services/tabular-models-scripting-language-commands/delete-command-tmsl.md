---
title: "Delete コマンド (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 05d3fb14-ea03-4596-ac2e-9ae5bab27b4d
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ef079032f26d5aa287b6e6ce30c87e7d1d1392a3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="delete-command-tmsl"></a>Delete コマンド (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  データベースまたは現在のデータベース内のオブジェクトを削除します。   
指定したオブジェクトとすべての子オブジェクトとコレクションを削除します。 オブジェクトが存在しない場合、コマンドは、エラーが発生します。  
  
## <a name="request"></a>要求  
 削除されるオブジェクトを指定するには、オブジェクトのパスを使用します。 たとえば、パーティションを削除するには、直前のテーブルおよびデータベース オブジェクトを指定することが必要です。  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",   
      "partition": "may2011"   
    }   
  }   
}   
```  
  
 次のオブジェクトを削除することができます。  
  
 [データベース オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016"  
    }   
  }   
}   
```  
  
 [データ ソース オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureworksDW2016",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    }  
  }  
}  
```  
  
 [Tables オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",  
    }   
  }   
}   
```  
  
 [パーティション オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "table": "Reseller Sales",   
      "partition": "may2011"   
    }   
  }   
}   
```  
  
 [ロール オブジェクト &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)  
  
```  
{   
  "delete": {   
    "object": {   
      "database": "AdventureworksDW2016",   
      "role": "Data Reader"  
    }   
  }   
}   
```  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="examples"></a>使用例  
 **例 1** -データベースを削除します。  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureWorksDW2016"  
    }  
  }  
}  
```  
  
 **例 2** -接続を削除します。  
  
```  
{  
  "delete": {  
    "object": {  
      "database": "AdventureWorksDW2016",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    }  
  }  
}  
```  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドの既製のスクリプトを生成できます。  たとえば、既存のデータベースを右クリックする >**スクリプト** > **データベースをスクリプト** > **を削除する**です。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください[表形式モデル スクリプト言語 &#40;です。TMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)新機能がサポートされているより明確にします。  

## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
