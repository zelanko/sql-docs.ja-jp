---
title: "データ ソース オブジェクト (TMSL) |Microsoft ドキュメント"
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
ms.assetid: 1357ae7e-30a4-481a-831c-7b046fe15aa4
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 13f647affa03844562f479223df57e1f8a2102f8
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="datasources-object-tmsl"></a>データ ソース オブジェクト (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
モデル、または DirectQuery モードを使用してクエリを通じて渡すことで、データを追加するインポート中にいずれかのモデルで使用されるデータ ソースへの接続を定義します。  DirectQuery モードでモデルを 1 つだけある**データソース**オブジェクト。  
  
 作成する場合、置換、またはデータ ソース オブジェクト自体を変更するには、(パーティション スクリプトなど)、スクリプトで参照されるすべてのデータ ソースがあります、既存場合を除き、**データソース**モデル内のオブジェクト。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトは、共通の名前、型、説明、プロパティのコレクション、および注釈を含むプロパティのセットを持ちます。 **DataSource**オブジェクトでは、次のプロパティもがあります。  
  
 型  
 DataSource の種類。 現時点は、唯一の有効な値は、プロバイダー (1) - 通常の接続文字列です。  
  
 connectionString  
 最小サーバーおよびデータベースを指定するデータ プロバイダーまたはユーザー アカウントなど、外部の RDBMS でサポートされているその他のプロパティを含めることも接続文字列。 この値は必須です。 参照してください[SqlConnectionStringBuilder クラス](https://msdn.microsoft.com/en-us/library/ms254500\(v=vs.110\).aspx)SQL Server の詳細については、データベース接続文字列プロパティです。  
  
 impersonationMode  
 Analysis Services は、クエリを要求するユーザーの id を偽装するかどうかを指定します。 このプロパティは、権限借用のために使用する資格情報を指定する数値です。 列挙値は次のとおりです。  
  
-   既定の (1) - サーバーは権限借用が使用されているコンテキストの適切なであると判断した偽装メソッドを使用します。  
  
-   ImpersonateAccount (2) - サーバーは、指定されたユーザー アカウントを使用します。  
  
-   ImpersonateAnonymous (3) - サーバーは、匿名ユーザー アカウントを使用します。  このオプションは、推奨されていませんが、認証を処理するカスタム アプリケーションで HTTP アクセスのシナリオでは使用します。  
  
-   ImpersonateCurrentUser (4) - サーバーは、として、クライアントが接続しているユーザー アカウントを使用します。  
  
-   ImpersonateServiceAccount (5): サーバーは、サーバーを実行しているユーザー アカウントを使用します。  
  
-   ImpersonateUnattendedAccount (6) – サーバーは、自動実行用ユーザー アカウントを使用します。 Power Pivot または表形式モデルの場合、SharePoint 環境で実行されているために使用します。  
  
 Analysis Services が、信頼された委任用に構成されている場合、DirectQuery モードは impersonateCurrentuser を使用できますか  
                      impersonateServiceAccount クエリ要求は、Analysis Services サービス アカウントのセキュリティ コンテキストで行われた場合。 参照してください[Configure Analysis Services for Kerberos の制約付き委任](../../analysis-services/instances/configure-analysis-services-for-kerberos-constrained-delegation.md)です。  
  
 account  
 権限借用のために使用します。 Windows またはデータベースがあるアカウントを持つ有効なログインに対する読み取り権限、外部データベース。  
  
 パスワード  
 アカウントのパスワードを提供する、暗号化された文字列。  
  
 maxConnections  
 データ ソースに対して同時に開く接続の最大数。  
  
 isolation  
 データ ソースに対してコマンドを実行するときに使用される分離の種類。 有効な値は ReadCommitted (1) とスナップショット (2) です。  
  
 timeout  
 データ ソースに対して実行されたコマンドに対する秒単位のタイムアウトを指定する整数。  
  
 プロバイダー (provider)  
 それ以外の場合、接続文字列で指定されていない場合に、リレーショナル データベースへの接続で使用されるマネージ データ プロバイダーの名前を識別する省略可能な文字列。  
  
## <a name="usage"></a>使用方法  
 **DataSource**オブジェクトを使用[Alter コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/alter-command-tmsl.md)、[コマンド &#40; を作成します。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/create-command-tmsl.md)、 [CreateOrReplace コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/createorreplace-command-tmsl.md)、[コマンド &#40; を削除TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/delete-command-tmsl.md)、[コマンド &#40; を更新TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/refresh-command-tmsl.md)、および[MergePartitions コマンド &#40;です。TMSL &#41;](../../analysis-services/tabular-models-scripting-language-commands/mergepartitions-command-tmsl.md).  
  
 A**データソース**オブジェクトは、モデルのプロパティですが、モデルとデータベース間の一対一のマッピングを指定されたデータベース オブジェクトのプロパティとして指定することもできます。  SQL クエリに基づき、パーティションを指定も、**データソース**、削減されたプロパティのセットでのみです。  
  
 作成する場合、置換、またはデータ ソース オブジェクトを変更することは、オブジェクト定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。  
  
## <a name="examples"></a>使用例  
 **例 1** -への接続、 *FoodMart*の名前付きインスタンス、リモート データベース*Sales*という名前のネットワーク サーバーに*Server01*です。  
  
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
 [インターネット インフォメーション サービス &#40;IIS"&"#41 です。 Analysis Services への HTTP アクセスを構成します。8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)  
  
  
