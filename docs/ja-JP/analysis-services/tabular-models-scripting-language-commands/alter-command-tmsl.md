---
title: Alter コマンド (TMSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 8bdc49f1-209e-4055-be19-c83862b81efa
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: aee73b9b0754fae9b801c6b66a4f635e7119e0ac
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="alter-command-tmsl"></a>Alter コマンド (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  既存のオブジェクトがその子ではありません、表形式モードで Analysis Services インスタンス上に変更します。  オブジェクトが存在しない場合、コマンドは、エラーが発生します。  
  
 使用して**Alter**コマンドを対象となる更新プログラム、すべての列も指定せずに、テーブルのプロパティの設定と同様にします。 このコマンドはのような**CreateOrReplace**、せずに完全なオブジェクトの定義を指定する必要があるなくなります。  
  
 すべての後、新しいまたは既存の値を指定する必要は、1 つの読み取り/書き込みプロパティを指定する場合は、読み取り/書き込みプロパティを持つオブジェクト。 AMO PowerShell を使用して、プロパティの一覧を取得することができます。 
  
## <a name="request"></a>要求  
 **Alter**任意の属性はありません。 入力には、変更、その後、変更されたオブジェクトの定義であるオブジェクトが含まれます。  
  
 次の例は、パーティション オブジェクトのプロパティを変更するための構文を示しています。 オブジェクトのパスを確立するパーティション オブジェクトが親オブジェクトの名前と値のペアを使用して変更されます。 2 番目の入力は、新しいプロパティ値を指定するパーティション オブジェクトです。  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "\<database-name>",   
      "table": "\<table-name>",   
      "partition": "\<partition-name>"   
    },   
    "partition": {   
      "name": "\<new-partition-name>",   
       . . .  << other properties   
    }   
  }   
}   
```  
  
 要求の構造は、オブジェクトによって異なります。 **Alter**次のオブジェクトのいずれかで使用できます。  
  
 [データベース オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)データベースの名前を変更します。  
  
```  
"alter": {   
    "object": {   
      "database": "\<database-name>"  
    },   
    "database": {   
      "name": "\<new-database-name>",   
    }   
  }   
```  
  
 [データ ソース オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md) 、これは、子オブジェクトのデータベースの接続の名前を変更します。  
  
```  
{   
   "alter":{   
      "object":{   
         "database":"AdventureWorksTabular1200",  
         "dataSource":"SqlServer localhost AdventureworksDW2016"  
      },  
      "dataSource":{   
         "name":"A new connection name"  
      }  
   }  
}  
```  
  
 [Tables オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)を参照してください**例 1**以下です。  
  
 [パーティション オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)を参照してください**例 2**以下です。  
  
 [ロール オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)ロール オブジェクトのプロパティを変更します。  
  
```  
{   
   "alter":{   
      "object":{   
         "database":"AdventureWorksTabular1200",  
         "role":"DataReader"  
      },  
      "role":{   
         "name":"New Name"  
      }  
   }  
}  
```  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="examples"></a>使用例  
 次の例では、Management Studio の XMLA ウィンドウに実行したりへの入力として使用できるスクリプト[Invoke ASCmd コマンドレット](../../analysis-services/powershell/invoke-ascmd-cmdlet.md)AMO PowerShell でします。  
  
 **例 1** -このスクリプトは、テーブルの名前プロパティを変更します。  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "AdventureWorksDW2016",   
      "table": "DimDate"  
    },   
    "table": {   
      "name": "DimDate2"  
    }   
  }   
}  
```  
  
 ローカルの名前付きインスタンスと仮定した場合 (インスタンス名が「表形式」) し、このコマンド、alter スクリプトが JSON ファイルが DimDate から DimDate2 にテーブル名を変更します。  
  
 `invoke-ascmd -inputfile '\\my-computer\my-shared-folder\altertablename.json' -server 'localhost\Tabular'`  
  
 **例 2** --このスクリプトは現在の年が前の年の年末の位置など、パーティションの名前を変更します。 必ずすべてのプロパティを指定してください。 移動すると**ソース**指定しないと、でした壊すことのすべての既存のパーティションの定義。  
  
 作成する場合、置換、またはデータ ソース オブジェクト自体を変更するには、(次のパーティションのスクリプトなど)、スクリプトで参照されるすべてのデータ ソースがあります、既存場合を除き、**データソース**モデル内のオブジェクト。 データ ソースを変更する必要がある場合は、別のステップとしてようにします。  
  
```  
{   
  "alter": {   
    "object": {   
      "database": "InternetSales",   
      "table": "DimDate",  
      "partition": "CurrentYear"  
    },   
    "partition": {   
      "name": "Year2009",  
       "source": {  
             "query":  "SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] WHERE [dbo].[DimDate].CalendarYear = 2009",  
              "dataSource": "SqlServer localhost AdventureworksDW2016"  
        }  
    }   
  }   
}  
```  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行&#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からは、このコマンドの既製のスクリプトを生成することはできません。 代わりに、例を使用して開始したり、独自に作成できます。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください ([表形式モデル スクリプト言語&#40;TMSL&#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) がサポートされているものより明確にします。  

## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
