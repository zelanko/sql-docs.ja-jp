---
title: パーティション オブジェクト (TMSL) |Microsoft ドキュメント
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
ms.assetid: df1da0d2-d824-42ba-b9dc-47fbd8edc10f
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bc820929603cadb400bd19f3afa4d04a6222fb89
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="partitions-object-tmsl"></a>パーティション オブジェクト (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  パーティション、またはテーブルの行セットの論理セグメントを定義します。 パーティションは、サンプル データ モデリング環境でまたは DirectQuery を使用してクエリを実行してパスの完全なデータ クエリ用のデータのインポートに使用される SQL クエリで構成されます。  
  
 パーティションのプロパティは、テーブルのデータを供給する方法を決定します。  オブジェクトの階層では、パーティションの親オブジェクトは、テーブル オブジェクトです。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトは、共通の名前、型、説明、プロパティのコレクション、および注釈を含むプロパティのセットを持ちます。 **パーティション**オブジェクトでは、次のプロパティもがあります。  
  
 型  
 パーティションの種類。 有効な値は、数値と、次に示します。  
  
-   に対してクエリを実行してクエリ (1)-このパーティションのデータを取得した、**データソース**です。 **データソース**model.bim ファイルに定義されているデータ ソースにする必要があります。  
  
-   計算 (2) – は計算式を実行することによって、このパーティションのデータが設定されます。  
  
-   更新操作の一部としてサーバーにデータの行セットをプッシュして (3) – このパーティションのデータが格納されません。  
  
 mode  
 パーティションのクエリ モードを定義します。 有効な値は**インポート**、 **DirectQuery**、または**既定**(継承)。 この値は必須です。  
  
|||  
|-|-|  
|**[インポート]**|要求がインポートされたデータを格納する、メモリ内分析エンジンに対して発行されるクエリを示します。|  
|**DirectQuery**|外部リレーショナル データベースにクエリを実行して渡します。 DirectQuery モードでは、パーティションを使用して、モデルのデザイン時に使用されるサンプル データを提供します。 実稼働サーバーに展開されると、完全データ ビューに切り替えてください。 DirectQuery モードには、1 つのテーブルの 1 つのパーティションとモデルごとに 1 つのデータ ソースが必要であることを思い出してください。|  
|**default**|モデルまたはデータベース レベルでのオブジェクト ツリーの上位のモードを切り替える場合は、これを設定します。 既定値を選択すると、クエリ モードになります import または DirectQuery。|  
  
 source  
 クエリを実行するデータの場所を識別します。 有効な値は**クエリ、計算**、または**none**です。 この値は必須です。  
  
|||  
|-|-|  
|**[なし]**|インポート モード、データの読み込みし、メモリに格納されている場所に使用されます。|  
|**query**|DirectQuery モードでは、これは、モデルの指定されたリレーショナル データベースに対して実行される SQL クエリ**データソース**です。 参照してください[データソース オブジェクト&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)です。|  
|**計算**|テーブルの作成時に指定された式から計算テーブルに基づいています。 この式は、計算テーブル用に作成されたパーティションのソースと見なされます。|  
  
 dataview  
 DirectQuery パーティションは、さらに、追加の dataView プロパティは、データを取得するクエリがサンプルか、完全なデータセットがかどうかを指定します。 有効な値は**完全**、**サンプル**、または**既定**(継承)。 前述のように、サンプルは、データ モデリングと、テスト中にのみ使用されます。 参照してください[デザイン モードで DirectQuery モデルにサンプル データを追加する](../../analysis-services/tabular-models/add-sample-data-to-a-directquery-model-in-design-mode.md)詳細についてはします。  
  
## <a name="usage"></a>使用方法  
 パーティション オブジェクトを使用[Alter コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)、[コマンドを作成して&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)、 [CreateOrReplace コマンド&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)、 [Delete コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)、 [Refresh コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)、および[MergePartitions コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 作成する場合、置換、またはパーティション オブジェクトを変更することは、オブジェクト定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。 読み取り/書き込みプロパティには、名前、説明、モード、およびソースが含まれます。  
  
## <a name="examples"></a>使用例  
 **例 1** -テーブル (ファクト テーブルではない) の単純なパーティション構造体。  
  
```  
"partitions": [  
          {  
            "name": "Customer",  
            "source": {  
              "query": "SELECT [dbo].[Customer].* FROM [dbo].[Customer]",  
              "dataSource": "SqlServer localhost FoodmartDB"  
            }  
]  
```  
  
 **例 2** - パーティションのファクト データは通常で、WHERE 句に基づいて、同じテーブルからデータの重複しないパーティションを作成します。  
  
```  
"partitions": [  
          {  
            "name": "sales_fact_2015",  
            "source": {  
              "query": "SELECT [dbo].[sales_fact_2015].* FROM [dbo].[sales_fact_2015] WHERE [dbo].[sales_fact_2015].[Quarter]=4",                                                                                          
              "dataSource": "SqlServer localhost FoodmartDB"  
            },  
          }  
        ]  
```  
  
 **例 3** -DAX 式に基づいて計算テーブル。  
  
```  
"partitions": [  
          {  
            "name": "CalcTable1",  
            "source": {  
              "type": "calculated",  
              "expression": "'Product Class'"  
            },  
            }  
]  
```  
  
## <a name="full-syntax"></a>完全な構文  
 パーティション オブジェクトのスキーマ表現を以下に示します。  
  
```  
"partitions": {  
                "type": "array",  
                "items": {  
                  "description": "Partition object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "description": {  
                      "anyOf": [  
                        {  
                          "type": "string"  
                        },  
                        {  
                          "type": "array",  
                          "items": {  
                            "type": "string"  
                          }  
                        }  
                      ]  
                    },  
                    "mode": {  
                      "enum": [  
                        "import",  
                        "directQuery",  
                        "default"  
                      ]  
                    },  
                    "dataView": {  
                      "enum": [  
                        "full",  
                        "sample",  
                        "default"  
                      ]  
                    },  
                    "source": {  
                      "anyOf": [  
                        {  
                          "description": "QueryPartitionSource object of Tabular Object Model (TOM)",  
                          "type": "object",  
                          "properties": {  
                            "type": {  
                              "enum": [  
                                "query",  
                                "calculated",  
                                "none"  
                              ]  
                            },  
                            "query": {  
                              "anyOf": [  
                                {  
                                  "type": "string"  
                                },  
                                {  
                                  "type": "array",  
                                  "items": {  
                                    "type": "string"  
                                  }  
                                }  
                              ]  
                            },  
                            "dataSource": {  
                              "type": "string"  
                            }  
                          },  
                          "additionalProperties": false  
                        },  
                        {  
                          "description": "CalculatedPartitionSource object of Tabular Object Model (TOM)",  
                          "type": "object",  
                          "properties": {  
                            "type": {  
                              "enum": [  
                                "query",  
                                "calculated",  
                                "none"  
                              ]  
                            },  
                            "expression": {  
                              "anyOf": [  
                                {  
                                  "type": "string"  
                                },  
                                {  
                                  "type": "array",  
                                  "items": {  
                                    "type": "string"  
                                  }  
                                }  
                              ]  
                            }  
                          },  
                          "additionalProperties": false  
                        }  
                      ]  
                    },  
                    "annotations": {  
                      "type": "array",  
                      "items": {  
                        "description": "Annotation object of Tabular Object Model (TOM)",  
                        "type": "object",  
                        "properties": {  
                          "name": {  
                            "type": "string"  
                          },  
                          "value": {  
                            "anyOf": [  
                              {  
                                "type": "string"  
                              },  
                              {  
                                "type": "array",  
                                "items": {  
                                  "type": "string"  
                                }  
                              }  
                            ]  
                          }  
                        },  
                        "additionalProperties": false  
                      }  
                    }  
                  },  
                  "additionalProperties": false  
                }  
              },  
  
```  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  
