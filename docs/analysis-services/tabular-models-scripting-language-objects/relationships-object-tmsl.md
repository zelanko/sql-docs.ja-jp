---
title: "リレーションシップ オブジェクト (TMSL) |Microsoft ドキュメント"
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
ms.assetid: 7588565f-ea34-4402-8be9-331188bdb8c2
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b54b8749604cd8a5a17ee219326d814dc76131c4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="relationships-object-tmsl"></a>リレーションシップ オブジェクト (TMSL)

[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

  基数を指定する機能をソースとターゲット テーブルとクエリとセキュリティ フィルターの方向の間のリレーションシップを定義します。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトは、共通の名前、型、説明、プロパティのコレクション、および注釈を含むプロパティのセットを持ちます。 **リレーションシップ**オブジェクトでは、次のプロパティもがあります。  
  
 isActive  
 リレーションシップがアクティブまたは非アクティブとしてマークされているかどうかを示すブール値。 アクティブなリレーションシップは、テーブル間のフィルター処理に自動的に使用されます。 非アクティブなリレーションシップは、USERELATIONSHIP 関数を使用して DAX 計算で明示的に使用できます。  
  
 crossFilteringBehavior  
 リレーションシップがデータのフィルター処理に及ぼす影響を示します。 参照してください[双方向クロス フィルターの SQL Server 2016 Analysis services 表形式モデル](../../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md)詳細についてはします。 有効な値は次のとおりです。  
  
-   OneDirection (1) - リレーションシップの"To"端で選択した行が自動的にフィルター処理、テーブル、リレーションシップの"From"端でのスキャンを実行します。  
  
-   BothDirections (2) - フィルターのリレーションシップの両端に自動的にテーブルをフィルター処理、他のです。  
  
-   自動 (3) のエンジンは、リレーションシップを分析し、ヒューリスティックを使用して、動作のいずれかを選択します。  
  
 joinOnDateBehavior  
 2 つの日時列を結合するときに、日付と時刻の両方を結合するか、または日付のみを結合するかを示します。  
  
-   DateAndTime (1) - 次の 2 つの日時列を結合する際に、日付と時刻の部分で結合します。  
  
-   DatePartOnly (2) の 2 つの日時列を結合する際に、日付部分のみで結合します。  
  
 relyOnReferentialIntegrity  
 使用されていません。将来使用するために予約されています。  
  
 securityFilteringBehavior  
 リレーションシップが及ぼす行レベルのセキュリティ式を評価するときに、データのフィルター処理を示す列挙です。 有効な値は次のとおりです。  
  
-   OneDirection (1) - リレーションシップの"To"端で選択した行が自動的にフィルター処理、テーブル、リレーションシップの"From"端でのスキャンを実行します。  
  
-   BothDirections (2) - フィルターのリレーションシップの両端に自動的にテーブルをフィルター処理、他のです。  
  
## <a name="usage"></a>使用方法  
 リレーションシップ オブジェクトを使用[Alter コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)、[コマンド &#40; を作成します。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)、 [CreateOrReplace コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)、および[コマンド &#40; を削除TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md).  
  
 作成する場合、置換、または、リレーションシップ オブジェクトを変更することは、オブジェクト定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。  
  
## <a name="full-syntax"></a>完全な構文  
 Relationship オブジェクトのスキーマ表現を以下に示します。  
  
```  
"relationships": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "SingleColumnRelationship object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "isActive": {  
                    "type": "boolean"  
                  },  
                  "type": {  
                    "enum": [  
                      "singleColumn"  
                    ]  
                  },  
                  "crossFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections",  
                      "automatic"  
                    ]  
                  },  
                  "joinOnDateBehavior": {  
                    "enum": [  
                      "dateAndTime",  
                      "datePartOnly"  
                    ]  
                  },  
                  "relyOnReferentialIntegrity": {  
                    "type": "boolean"  
                  },  
                  "securityFilteringBehavior": {  
                    "enum": [  
                      "oneDirection",  
                      "bothDirections"  
                    ]  
                  },  
                  "fromCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "toCardinality": {  
                    "enum": [  
                      "none",  
                      "one",  
                      "many"  
                    ]  
                  },  
                  "fromColumn": {  
                    "type": "string"  
                  },  
                  "fromTable": {  
                    "type": "string"  
                  },  
                  "toColumn": {  
                    "type": "string"  
                  },  
                  "toTable": {  
                    "type": "string"  
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
            ]  
          }  
        }  
```  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [リレーションシップの作成](../../integration-services/data-flow/transformations/create-relationships.md)  
  
  
