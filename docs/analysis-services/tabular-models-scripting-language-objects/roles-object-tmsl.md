---
title: "ロール オブジェクト (TMSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1812f60b-bd5f-417c-96bc-3d834bdb4d3c
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 257ead3072f8b359bff275709ee372483989fccf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="roles-object-tmsl"></a>ロール オブジェクト (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]権限のコレクションを指定する、モデルのロールを定義します。 ロールのメンバーシップは、Windows セキュリティ プリンシパルで構成されます。 特定のオブジェクトへのアクセスを制限するロールでは、フィルターを設定できます。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトは、共通の名前、型、説明、プロパティのコレクション、および注釈を含むプロパティのセットを持ちます。 **ロール**オブジェクトでは、次のプロパティもがあります。  
  
 modelPermission  
 データベースに対する権限のスコープを設定します。 有効な値は、none、  
                  読み取り、  
                  readRefresh、  
                  更新します。  
                  および管理者。 参照してください[ロールとアクセス許可 &#40;です。Analysis Services &#41;](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)データベース アクセス許可についてはします。  
  
 メンバー  
 メンバーは、メンバーの名前と ID、メンバーの名前が別名データ型または Windows セキュリティの方針のフレンドリ名、ID は、セキュリティ識別子の両方で構成されます。 ロールの定義の両方を指定します。参照してください[SID コンポーネント](https://msdn.microsoft.com/en-us/library/windows/desktop/aa379597\(v=vs.85\).aspx)識別子の詳細についてはします。  
  
 テーブル アクセス許可  
 テーブルのアクセス許可は、DAX 式を使用して定義されているアクセス許可を持つ名前付きオブジェクトです。 このプロパティは省略可能でセキュリティ フィルターを適用するために使用します。  
  
## <a name="usage"></a>使用方法  
 **ロール**オブジェクトを使用[Alter コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)、[コマンド &#40; を作成します。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)、 [CreateOrReplace コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)、および[コマンド &#40; を削除TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md).  
  
 A**ロール**オブジェクトは、モデルのプロパティですが、モデルとデータベース間の一対一のマッピングを指定されたデータベース オブジェクトのプロパティとして指定することもできます。  
  
 作成する場合、置換、またはロール オブジェクトを変更することは、オブジェクト定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。  
  
## <a name="full-syntax"></a>完全な構文  
 モデルのロール オブジェクトのスキーマ表現を以下に示します。  
  
```  
"roles": {  
          "type": "array",  
          "items": {  
            "description": "ModelRole object of Tabular Object Model (TOM)",  
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
              "modelPermission": {  
                "enum": [  
                  "none",  
                  "read",  
                  "readRefresh",  
                  "refresh",  
                  "administrator"  
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
              },  
              "members": {  
                "type": "array",  
                "items": {  
                  "anyOf": [  
                    {  
                      "description": "WindowsModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
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
                    },  
                    {  
                      "description": "ExternalModelRoleMember object of Tabular Object Model (TOM)",  
                      "type": "object",  
                      "properties": {  
                        "memberName": {  
                          "type": "string"  
                        },  
                        "memberId": {  
                          "type": "string"  
                        },  
                        "identityProvider": {  
                          "type": "string"  
                        },  
                        "memberType": {  
                          "enum": [  
                            "auto",  
                            "user",  
                            "group"  
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
                  ]  
                }  
              },  
              "tablePermissions": {  
                "type": "array",  
                "items": {  
                  "description": "TablePermission object of Tabular Object Model (TOM)",  
                  "type": "object",  
                  "properties": {  
                    "name": {  
                      "type": "string"  
                    },  
                    "filterExpression": {  
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
              }  
            },  
            "additionalProperties": false  
          }  
        }  
```  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [ロールと権限 (Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md)  
  
  
