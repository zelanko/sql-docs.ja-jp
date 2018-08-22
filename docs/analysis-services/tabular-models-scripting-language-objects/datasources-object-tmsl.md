---
title: データ ソース オブジェクト (TMSL) |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0a83ac3429a3012269a35c64ba5fdcbec18b2d4c
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393954"
---
# <a name="datasources-object-tmsl"></a>DataSources オブジェクト (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  モデルまたは DirectQuery モードを使用して、クエリ パスでは、データを追加するインポート中にいずれかのモデルで使用されるデータ ソースへの接続を定義します。  DirectQuery モードのモデルのいずれかができますのみ**DataSource**オブジェクト。  
  
 作成、置換、またはデータ ソース オブジェクト自体を変更するには、任意のデータ ソース (パーティション スクリプトなど)、スクリプトで参照されている必要があります、既存場合を除き、 **DataSource**モデル内のオブジェクト。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトには、名前、型、説明、プロパティのコレクション、および注釈を含むプロパティの共通セットがあります。 **DataSource**オブジェクトでは、次のプロパティもがあります。  
  
 type  
 DataSource の種類。 現時点では、唯一の有効な値は、プロバイダー (1) の通常の接続文字列です。  
  
 connectionString  
 接続文字列を最小限のデータベースとサーバーを指定しますが、データ プロバイダーまたはユーザー アカウントなど、外部の RDBMS でサポートされるその他のプロパティを含めることもできます。 この値は必須です。 参照してください[SqlConnectionStringBuilder クラス](/dotnet/framework/data/adonet/connection-string-syntax)詳細については、SQL Server データベースの接続文字列プロパティ。  
  
 impersonationMode  
 Analysis Services がクエリを要求するユーザーの id を偽装する必要があるかどうかを指定します。 このプロパティは、偽装に使用する資格情報を指定する数値です。 列挙値は次のとおりです。  
  
-   既定の (1) - サーバーは権限借用が使用されているコンテキストに適したすると判断した偽装メソッドを使用します。  
  
-   ImpersonateAccount (2) - サーバーは、指定したユーザー アカウントを使用します。  
  
-   ImpersonateAnonymous (3) - サーバーは、匿名ユーザー アカウントを使用します。  このオプションは推奨されませんが、認証を処理するカスタム アプリケーションで HTTP アクセスのシナリオで使用される場合があります。  
  
-   ImpersonateCurrentUser (4) - サーバーは、として、クライアントが接続しているユーザー アカウントを使用します。  
  
-   ImpersonateServiceAccount (5) - サーバーは、ユーザー アカウントとして実行しているサーバーを使用します。  
  
-   ImpersonateUnattendedAccount (6): サーバーは、自動ユーザー アカウントを使用します。 これは、SharePoint 環境で実行される Power Pivot または表形式モデルに使用されます。  
  
 Analysis Services が、信頼された委任用に構成された場合、DirectQuery モードは impersonateCurrentuser を使用できますか  
                      impersonateServiceAccount クエリ要求が、Analysis Services サービス アカウントのセキュリティ コンテキストで行われた場合。 参照してください[Configure Analysis Services for Kerberos の制約付き委任](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md)します。  
  
 account  
 権限借用に使用されます。 Windows またはデータベース アカウントを持つ有効なログインを持つ外部データベースのアクセス許可の読み取り。  
  
 password  
 アカウントのパスワードを提供する、暗号化された文字列。  
  
 maxConnections  
 データ ソースに対して同時に開く接続の最大数。  
  
 isolation  
 データ ソースに対してコマンドを実行するときに使用される分離の種類。 有効な値は ReadCommitted (1) またはスナップショット (2) です。  
  
 timeout  
 データ ソースに対して実行されたコマンドに対する秒単位のタイムアウトを指定する整数。  
  
 provider  
 それ以外の場合、接続文字列で指定されていない場合に、リレーショナル データベースへの接続で使用されるマネージ データ プロバイダーの名前を識別する省略可能な文字列。  
  
## <a name="usage"></a>使用方法  
 **DataSource**オブジェクトを使用[Alter コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)、[コマンドを作成する&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)、 [CreateOrReplace コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)、 [Delete コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)、 [Refresh コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)、および[MergePartitions コマンド&#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md)します。  
  
 A **DataSource**オブジェクトは、モデルのプロパティですが、モデルとデータベース間の一対一のマッピングを指定したデータベース オブジェクトのプロパティとして指定することもできます。  SQL クエリに基づくパーティションを指定も、 **DataSource**プロパティの制限のセットでのみです。  
  
 作成する場合、置換、または、データ ソース オブジェクトを変更することは、オブジェクトの定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。  
  
## <a name="examples"></a>使用例  
 **例 1** -への接続、 *FoodMart*名前付きインスタンスのリモートのデータベース*Sales*という名前のネットワーク サーバー *Server01*します。  
  
```  
"dataSources": [  
      {  
        "name": "SqlServer Server01 FoodMart",  
        "connectionString": "Provider=SQLNCLI11;Data Source=Server01\Sales;Initial Catalog=Foodmart;Integrated Security=SSPI;Persist Security Info=false",  
        "impersonationMode": "impersonateServiceAccount",  
      }  
]  
```  
  
## <a name="full-syntax"></a>完全な構文  
 モデルのデータ ソース オブジェクトのスキーマ表現を以下に示します。  
  
```  
"dataSources": {  
          "type": "array",  
          "items": {  
            "anyOf": [  
              {  
                "description": "ProviderDataSource object of Tabular Object Model (TOM)",  
                "type": "object",  
                "properties": {  
                  "name": {  
                    "type": "string"  
                  },  
                  "description": {  
                    "type": "string"  
                  },  
                  "type": {  
                    "enum": [  
                      "provider"  
                    ]  
                  },  
                  "connectionString": {  
                    "type": "string"  
                  },  
                  "impersonationMode": {  
                    "enum": [  
                      "default",  
                      "impersonateAccount",  
                      "impersonateAnonymous",  
                      "impersonateCurrentUser",  
                      "impersonateServiceAccount",  
                      "impersonateUnattendedAccount"  
                    ]  
                  },  
                  "account": {  
                    "type": "string"  
                  },  
                  "password": {  
                    "type": "string"  
                  },  
                  "maxConnections": {  
                    "type": "integer"  
                  },  
                  "isolation": {  
                    "enum": [  
                      "readCommitted",  
                      "snapshot"  
                    ]  
                  },  
                  "timeout": {  
                    "type": "integer"  
                  },  
                  "provider": {  
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
        },  
  
```  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [DirectQuery モード](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)   
 [インターネット インフォメーション サービス (IIS) 8.0 上の Analysis Services への HTTP アクセスの構成](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
