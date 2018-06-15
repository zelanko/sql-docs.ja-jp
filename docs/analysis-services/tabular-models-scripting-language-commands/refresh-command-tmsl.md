---
title: Refresh コマンド (TMSL) |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db07b1a5b4dc98b516e2f15e29aced3c74a57a16
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34043696"
---
# <a name="refresh-command-tmsl"></a>Refresh コマンド (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  現在のデータベース内のオブジェクトを処理します。   
**更新**常に並列で実行を調整する場合を除き、[コマンドのシーケンス&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/sequence-command-tmsl.md)です。  
  
 データ更新操作中に、一部のオブジェクトの一部のプロパティをオーバーライドできます。  
  
-   変更、 **QueryDefinition**のプロパティ、**パーティション**その場でフィルター式を使用してデータをインポートするオブジェクト。  
  
-   一部としてデータ ソースの資格情報を提供する**更新**コマンドを**ConnectionString**のプロパティ、**データソース**オブジェクト。 このアプローチでしたすると見なさより安全な資格情報が提供され、操作の間で一時的に使用ではなく格納されています。  
  
 これらのプロパティの上書きの図解は、このトピックの例を参照してください。  
  
> [!NOTE]  
>  マルチ ディメンションの処理とは異なりは、表形式処理でエラーの処理の特別な処理はありません。  

  
## <a name="request"></a>要求  
 **更新**型のパラメーターとオブジェクトの定義を取得します。  
  
```  
    {  
        "refresh": {  
            "description": "Parameters of Refresh command of Analysis Services JSON API",  
            "properties": {  
            "type": {  
                "enum": [  
                "full",  
                "clearValues",  
                "calculate",  
                "dataOnly",  
                "automatic",  
                "add",  
                "defragment"  
                ]  
            },  
            "objects": {  
. . .   
```  
  
 **型**パラメーターが、処理操作のスコープを設定します。  
  
||||  
|-|-|-|  
|**更新の種類**|**適用されます。**|**Description**|  
|完全|データベース、<br />テーブル、<br />パーティション|指定されたパーティション、テーブル、データベースのすべてのパーティションに対して、データが更新され、すべての依存が再計算されます。 計算パーティションに対して、パーティションとそのすべての依存を再計算します。|  
|clearValues|データベース、<br />テーブル、<br />パーティション|このオブジェクトとそのすべての依存の値をクリアします。|  
|計算|データベース、<br />テーブル、<br />パーティション|必要な場合にのみ、このオブジェクトとそのすべての依存を再計算します。 この値は、揮発性の数式を除き、再計算を強制しません。|  
|dataOnly|データベース、<br />テーブル、<br />パーティション|このオブジェクトのデータを更新し、すべての依存をクリアします。|  
|automatic|データベース、<br />テーブル、<br />パーティション|オブジェクトを更新し、再計算する必要がある場合、オブジェクトとそのすべての依存を更新し、再計算します。 パーティションの状態が準備完了以外の場合に適用されます。|  
|add|パーティション|このパーティションにデータを追加し、すべての依存を再計算します。 このコマンドは通常のパーティションにのみ有効であり、計算パーティションでは利用できません。|  
|断片化を解消します。|データベース、<br />Table|指定されたテーブル内のデータを最適化します。 データがテーブルに追加されるか、テーブルから削除されると、各列のディクショナリに、実際の列値にはもう存在しない値が入力されることがあります。 最適化オプションを利用すると、使用されなくなったディクショナリの値が消去されます。|  
  
 次のオブジェクトを更新することができます。  
  
 [データベース オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)データベースを処理します。  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200"  
      }  
    ]  
  }  
}  
```  
  
 [Tables オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md) 1 つのテーブルを処理します。  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "Date"  
      }  
    ]  
  }  
}  
```  
  
 [パーティション オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)テーブル内の 1 つのパーティションを処理します。  
  
```  
{  
  "refresh": {  
    "type": "automatic",  
    "objects": [  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota"  
      },  
      {  
        "database": "AdventureWorksTabular1200",  
        "table": "FactSalesQuota",  
        "partition": "FactSalesQuota - 2011"  
      }  
    ]  
  }  
}  
```  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="examples"></a>使用例  
 両方を上書き、 **ConnectionString**およびパーティションの定義をクエリします。  
  
```  
{   
    "refresh": {   
        "type": "data",   
        "objects": [   
            {   
                "database": "tmtestdb",   
                "table": "sales"   
            },   
            {   
                "database": "tmtestdb",   
                "table": "customer"   
            }   
        ],   
        "overrides": [   
            {   
                "dataSources": [ // Bindings for Data Sources   
                    {   
                        "object": {   
                            "database": "tmtestdb",   
                            "dataSource": "contoso"   
                        },   
                        "dataSource": {   
                        "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=contoso;Integrated Security=SSPI;Persist Security Info=false"   
"   
                        }   
                    }   
                ],   
                "partitions": [ // Bindings for Partitions   
                    {   
                        "object": {   
                            "database": "tmtestdb",   
                            "table": "sales",   
                            "partition": "2015"   
                        },   
                        "partition": {   
                            "source": {   
                                "query": [  
                                     "SELECT sales.salesamount, customer.customername FROM sales",  
                                     "JOIN customer on custKey = sales.custkey",  
                                     "JOIN date on date.DateKey = customer.OrderDate",  
                                     "WHERE date.CalendarYear='2015'"  
                                  ],  
                            }   
                        }   
                    }   
                ]   
            }   
        ]   
    }   
}   
```  
  
 型パラメーターを設定して特定のスコープよりも優先、 **dataOnly** 、更新メタデータはそのまま残ります。  
  
```  
{   
        "refresh" : {   
            "type" : "dataOnly",   
            "objects" : [   
                {   
                    "database" : "TMTestDB",   
                    "table" : "Customer"   
                },   
                {   
                    "database" : "TMTestDB",   
                    "table" : "Sales"   
                }   
            ],   
            "overrides" : [{   
                "scope" : {   
                    "database" : "TMTestDB",   
                    "table" : "Sales"   
                },   
                "dataSources" : [{   
                    "originalObject" : {   
                        "dataSource" : "SqlServer sqlcldb2 AS_foodmart_2000"   
                    },   
                    "connectionString" : "Provider=SQLNCLI11;Data Source=sqlcldb2;Initial Catalog=AS_foodmart_2000;Integrated Security=SSPI;Persist Security Info=false"   
                }]   
            }]   
        }   
    }   
```  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行&#40;XMLA&#41; ](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドの既製のスクリプトを生成できます。  たとえば、クリックして、**スクリプト**処理 ダイアログ ボックス。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください ([表形式モデル スクリプト言語&#40;TMSL&#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)) がサポートされているものより明確にします。  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [処理オプションと設定&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)  
  
  
