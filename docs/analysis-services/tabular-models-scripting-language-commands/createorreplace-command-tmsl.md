---
title: "CreateOrReplace コマンド (TMSL) |Microsoft ドキュメント"
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
ms.assetid: f77a0e04-461a-4fa8-b997-78057e410d56
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 62d90be2b4fe8aea96534c7c4d8b2b4617ac1ea1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="createorreplace-command-tmsl"></a>CreateOrReplace コマンド (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  作成するか、指定したオブジェクトと指定されているすべての子オブジェクトを置き換えます。 存在しないオブジェクトが作成されます。 既存のオブジェクトは、新しい定義に置き換えられます。  
  
 読み取り/書き込みプロパティを指定するには、それらすべてを含めることを確認してください。 読み取り/書き込みオブジェクトがない場合は、削除であると見なされます。  
  
## <a name="request"></a>要求  
 要求の構造は、オブジェクトによって異なります。 親であるオブジェクトがすべての子、兄弟と親の完全なオブジェクトの定義は必要ありませんがあります。  
  
 [データベース オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)  
  
 既存のデータベースをその名前、モデルが変更されたプロパティ、および接続を指定する名前が変更された、最小限のデータベース定義に置き換えます。 テーブル、パーティション、またはリレーションシップ オブジェクトの定義に含まれていないと、これらすべてのオブジェクトが削除されます。  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "TestCreateOrReplaceDB",  
      "id": "newID",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "import",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ]  
      }  
    }  
  }  
}  
```  
  
 [データ ソース オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)接続名が置き換えられます。  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "TestCreateOrReplaceDB",  
      "dataSource": "SqlServer localhost AdventureworksDW2016"  
    },  
    "dataSource": {  
      "name": "New connection name",  
      "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
      "impersonationMode": "impersonateAccount",  
      "account": "   ",  
      "annotations": [  
        {  
          "name": "ConnectionEditUISource",  
          "value": "SqlServer"  
        }  
      ]  
    }  
  }  
}  
```  
  
 [Tables オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)指定された 1 つだけを残して、既存のテーブルが上書きされます。  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "AdventureWorksTabular1200",  
      "id": "New-AdventureWorksTabular1200",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "import",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ],  
        "tables": [  
          {  
            "name": "Date",  
            "columns": [  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FullDateAlternateKey",  
                "dataType": "dateTime",  
                "sourceColumn": "FullDateAlternateKey",  
                "formatString": "General Date",  
                "sourceProviderType": "DBDate"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimDate",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimDate"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          }  
        ]  
     }  
   }  
 }  
}   
```  
  
 [パーティション オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)  
  
 パーティション名に置き換えます。 パーティションのオブジェクトが 3 つの読み取り/書き込みプロパティを持つ: ソースの名前を説明します。 読み取り/書き込みプロパティを指定するには、それらすべてを含めることを確認してください。 読み取り/書き込みオブジェクトがない場合は、削除であると見なされます。  
  
 オブジェクトの定義は、パーティションであるため、名前付きパーティションのみとその定義に影響します。 その他のテーブル、リレーションシップ、およびパーティションは影響を受けません。  
  
 作成する場合、置換、またはデータ ソース オブジェクト自体を変更するには、(次のパーティションのスクリプトなど)、スクリプトで参照されるすべてのデータ ソースがあります、既存場合を除き、**データソース**モデル内のオブジェクト。 データ ソースを変更する必要がある場合に追加します。  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200",  
      "table": "FactSalesQuota",  
      "partition": "FactSalesQuota - 2011"  
    },  
    "partition": {  
      "name": "Sales Quota for 2011",  
      "mode": "import",  
      "dataView": "full",  
      "source": {  
        "query": [  
          "SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
          "JOIN DimDate as DD",  
          "on DD.DateKey = FactSalesQuota.DateKey",  
          "WHERE DD.CalendarYear='2011'"  
        ],  
        "dataSource": "SqlServer localhost AdventureworksDW2016"  
      }  
    }  
  }  
}  
```  
  
 [ロール オブジェクト & #40 です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)メンバーを含む 1 つのロールの定義に置換します。  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200",  
      "role": "DataReader"  
    },  
    "role": {  
      "name": "DataReader",  
      "modelPermission": "read",  
      "members": [  
        {  
          "memberName": "ADVENTUREWORKS\\InternalSalesGrp"  
        }  
      ]  
    }  
  }  
}  
```  
  
## <a name="response"></a>応答  
 コマンドが成功した場合は、空の結果を返します。 それ以外の場合、XMLA 例外が返されます。  
  
## <a name="examples"></a>使用例  
 **例 1** -同じ名前の既存のデータベースを上書きして、新しいデータベースを作成します。  
  
```  
{  
  "createOrReplace": {  
    "object": {  
      "database": "AdventureWorksTabular1200"  
    },  
    "database": {  
      "name": "AdventureWorksTabular1200",  
      "id": "AdventureWorksTabular1200",  
      "compatibilityLevel": 1200,  
      "model": {  
        "defaultMode": "directQuery",  
        "culture": "en-US",  
        "dataSources": [  
          {  
            "name": "SqlServer localhost AdventureworksDW2016",  
            "connectionString": "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureworksDW2016;Integrated Security=SSPI;Persist Security Info=false",  
            "impersonationMode": "impersonateAccount",  
            "account": "   ",  
            "annotations": [  
              {  
                "name": "ConnectionEditUISource",  
                "value": "SqlServer"  
              }  
            ]  
          }  
        ],  
        "tables": [  
          {  
            "name": "DimDate",  
            "columns": [  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FullDateAlternateKey",  
                "dataType": "dateTime",  
                "sourceColumn": "FullDateAlternateKey",  
                "formatString": "General Date",  
                "sourceProviderType": "DBDate"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimDate",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimDate].* FROM [dbo].[DimDate] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimDate"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          },  
          {  
            "name": "DimEmployee",  
            "columns": [  
              {  
                "name": "EmployeeKey",  
                "dataType": "int64",  
                "sourceColumn": "EmployeeKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "SalesTerritoryKey",  
                "dataType": "int64",  
                "sourceColumn": "SalesTerritoryKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "FirstName",  
                "dataType": "string",  
                "sourceColumn": "FirstName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "LastName",  
                "dataType": "string",  
                "sourceColumn": "LastName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "MiddleName",  
                "dataType": "string",  
                "sourceColumn": "MiddleName",  
                "sourceProviderType": "WChar"  
              },  
              {  
                "name": "SalesPersonFlag",  
                "dataType": "boolean",  
                "sourceColumn": "SalesPersonFlag",  
                "formatString": "\"TRUE\";\"TRUE\";\"FALSE\"",  
                "sourceProviderType": "Boolean"  
              },  
              {  
                "name": "DepartmentName",  
                "dataType": "string",  
                "sourceColumn": "DepartmentName",  
                "sourceProviderType": "WChar"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "DimEmployee",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[DimEmployee].* FROM [dbo].[DimEmployee] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[DimEmployee].* FROM [dbo].[DimEmployee] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "DimEmployee"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          },  
          {  
            "name": "FactSalesQuota",  
            "columns": [  
              {  
                "name": "SalesQuotaKey",  
                "dataType": "int64",  
                "sourceColumn": "SalesQuotaKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "EmployeeKey",  
                "dataType": "int64",  
                "sourceColumn": "EmployeeKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "DateKey",  
                "dataType": "int64",  
                "sourceColumn": "DateKey",  
                "sourceProviderType": "Integer"  
              },  
              {  
                "name": "CalendarYear",  
                "dataType": "int64",  
                "sourceColumn": "CalendarYear",  
                "sourceProviderType": "SmallInt"  
              },  
              {  
                "name": "SalesAmountQuota",  
                "dataType": "decimal",  
                "sourceColumn": "SalesAmountQuota",  
                "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",  
                "sourceProviderType": "Currency",  
                "annotations": [  
                  {  
                    "name": "Format",  
                    "value": "\<Format Format=\"Currency\" Accuracy=\"2\" ThousandSeparator=\"True\">\<Currency LCID=\"1033\" DisplayName=\"$ English (United States)\" Symbol=\"$\" PositivePattern=\"0\" NegativePattern=\"0\" /></Format>"  
                  }  
                ]  
              },  
              {  
                "name": "Date",  
                "dataType": "dateTime",  
                "sourceColumn": "Date",  
                "formatString": "General Date",  
                "sourceProviderType": "DBTimeStamp"  
              }  
            ],  
            "partitions": [  
              {  
                "name": "FactSalesQuota",  
                "dataView": "full",  
                "source": {  
                  "query": " SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota] ",  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                }  
              },  
              {  
                "name": "FactSalesQuota - 2011",  
                "mode": "import",  
                "dataView": "sample",  
                "source": {  
                  "query": [  
                    "SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
                    "JOIN DimDate as DD",  
                    "on DD.DateKey = FactSalesQuota.DateKey",  
                    "WHERE DD.CalendarYear='2011'"  
                  ],  
                  "dataSource": "SqlServer localhost AdventureworksDW2016"  
                },  
                "annotations": [  
                  {  
                    "name": "QueryEditorSerialization",  
                    "value": [  
                      "\<?xml version=\"1.0\" encoding=\"UTF-16\"?>\<Gemini xmlns=\"QueryEditorSerialization\"><AnnotationContent><![CDATA[<RSQueryCommandText>SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota]",  
                      "JOIN DimDate as DD",  
                      "on DD.DateKey = FactSalesQuota.DateKey",  
                      "WHERE DD.CalendarYear='2011'</RSQueryCommandText><RSQueryCommandType>Text</RSQueryCommandType><RSQueryDesignState></RSQueryDesignState>]]></AnnotationContent></Gemini>"  
                    ]  
                  }  
                ]  
              }  
            ],  
            "annotations": [  
              {  
                "name": "_TM_ExtProp_QueryDefinition",  
                "value": " SELECT [dbo].[FactSalesQuota].* FROM [dbo].[FactSalesQuota] "  
              },  
              {  
                "name": "_TM_ExtProp_DbTableName",  
                "value": "FactSalesQuota"  
              },  
              {  
                "name": "_TM_ExtProp_DbSchemaName",  
                "value": "dbo"  
              }  
            ]  
          }  
        ],  
        "relationships": [  
          {  
            "name": "4426b078-193f-4a59-bc52-33f990bfb7da",  
            "fromTable": "FactSalesQuota",  
            "fromColumn": "DateKey",  
            "toTable": "DimDate",  
            "toColumn": "DateKey"  
          },  
          {  
            "name": "cde1e139-4553-4d0a-a025-1cd98e35aab2",  
            "fromTable": "FactSalesQuota",  
            "fromColumn": "EmployeeKey",  
            "toTable": "DimEmployee",  
            "toColumn": "EmployeeKey"  
          }  
        ]  
      }  
    }  
  }  
}  
  
```  
  
## <a name="usage-endpoints"></a>使用状況 (エンドポイント)  
 このコマンドの要素がのステートメントで使用される、[メソッドの実行 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)呼び出しで、次の方法で公開される XMLA エンドポイント。  
  
-   SQL Server Management Studio (SSMS) での XMLA ウィンドウとして  
  
-   入力ファイルとして、**呼び出す ascmd** PowerShell コマンドレット  
  
-   SSIS タスクまたは SQL Server エージェント ジョブへの入力として  
  
 SSMS からこのコマンドの既製のスクリプトを生成できます。  たとえば、既存のデータベースを右クリックする >**スクリプト** > **データベースをスクリプト** > **作成または置換する**です。  
  
 [ \[MS-t SSAS\]: QL Server Analysis Services Tabular (SQL Server の技術的なプロトコル)](http://go.microsoft.com/fwlink/p/?LinkId=784855) JSON 表形式メタデータ コマンドとオブジェクトの構造を説明するセクション 3.1.5.2.2 がドキュメントに含まれています。 現時点では、そのドキュメントでは、コマンドや TMSL スクリプトで実装されていない機能について説明します。 トピックを参照してください[表形式モデル スクリプト言語 & #40 です。TMSL &#41;参照](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)明確にする新機能がサポートされている.  

## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

