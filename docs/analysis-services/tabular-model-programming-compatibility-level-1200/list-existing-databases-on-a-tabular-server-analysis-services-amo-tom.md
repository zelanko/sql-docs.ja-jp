---
title: 表形式サーバー (Analysis Services AMO-TOM) 上の既存のデータベースを一覧表示 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ab5eb4b8-6254-442d-a42e-2372c346d260
caps.latest.revision: 2
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5386b96d66de38d29909eb4fbf5fb3498c01daec
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="list-existing-databases-on-a-tabular-server-analysis-services-amo-tom"></a>表形式サーバー (Analysis Services AMO-TOM) 上の既存のデータベースを一覧表示します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
ある場合、**サーバー**オブジェクトを Analysis Services インスタンスに接続していることができますを反復処理する**Server.Databases**分析サービスのインスタンスによってホストされているすべてのデータベースを一覧表示するコレクション。 

**Server.Databases**コレクションが 1 つを含む**データベース**サーバー モード (多次元または表形式) またはデータベースの種類 (多次元に関係なく、サーバーでホストされているすべてのデータベース オブジェクトプレ-1200 の表形式または Tabular 1200 以降)。 

使用してデータベースの種類をチェックする**Database.StorageEngineUsed**プロパティです。  

表形式の 1200 以降のデータベースでは、null 以外を返します**Database.Model**すべて表形式メタデータ オブジェクトへのアクセスを提供するプロパティ: テーブル、列、リレーションシップ、およびなどです。  

多次元の 1103 テーブルと、Database.Model 下プロパティが null になります。 ここでは、表ではないメタデータは 多次元プロパティ (など Database.Cubes Database.Dimensions) を使用できますではなくそれらのプロパティが (AMO) から Microsoft.AnalysisServices.Database クラスによって公開のみTOM) (Microsoft.AnalysisServices.Tabular.Database です。 データベースに使用するクラスの詳細については、次を参照してください。[これをインストールすると、配布、および、TOM クライアント ライブラリを参照する](../../analysis-services/tabular-model-programming-compatibility-level-1200/install-distribute-and-reference-the-tabular-object-model.md)です。

Database.StorageEngineUsed を TabularMetadata に設定すると、しない限り、アクセスまたはモデル ツリーを操作する表形式の名前空間内の他のクラスを使用することはできません。 

次の表は、サーバーまたはサーバーまたはデータベースで Microsoft.AnalysisServices.Tabular クラスを使用してデータベースに接続するときの動作をまとめたものです。 

mode | Database.model | Database.StorageEngineUsed
-----|----------------|---------------------------
表形式の 1200 1400 | モデルの名前を返します| StorageEngineUsed.TabularMetadata 
1103 のテーブル、1100、1050 | Null を返します | StorageEngineUsed.InMemory 
多次元 | Null を返します | StorageEngineUsed.Traditional 

## <a name="code-example-list-existing-databases"></a>コードの例: 既存のデータベースを一覧表示

次のコードは、サーバーでホストされるサーバーおよびリストのデータベースに接続する方法を示しています。 

```
using System; using Microsoft.AnalysisServices; 
using Microsoft.AnalysisServices.Tabular; 

 
namespace TOMSamples 
{ 
    class Program 
    { 
        static void Main(string[] args) 
        { 
            // 
            // Connect to the local default instance of Analysis Services 
            // 
            string ConnectionString = "DataSource=localhost"; 

             // 
            // The using syntax ensures the correct use of the 
            // Microsoft.AnalysisServices.Tabular.Server object. 
            // 
            using (Server server = new Server()) 
            { 
                server.Connect(ConnectionString); 

                 // 
                // List common properties for the databases on the server. 
                // 
                foreach (Database db in server.Databases) 
                { 
                    Console.WriteLine("Properties for database {0}:", db.Name); 
                    Console.ForegroundColor = ConsoleColor.Yellow; 
                    Console.WriteLine("Database ID:\t\t\t{0}", db.ID); 
                    Console.WriteLine("Database compatibility level:\t{0}", db.CompatibilityLevel); 
                    Console.WriteLine("Database collation:\t\t{0}", db.Collation); 
                    Console.WriteLine("Database created timestamp:\t{0}", db.CreatedTimestamp); 
                    Console.WriteLine("Database language ID:\t\t{0}", db.Language); 
                    Console.WriteLine("Database model type:\t\t{0}", db.ModelType); 
                    Console.WriteLine("Database state:\t\t\t{0}", db.State); 
                    Console.ResetColor(); 
                    Console.WriteLine(); 
                } 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```


## <a name="get-an-item-from-a-database"></a>データベースから取得する項目 

次のコード スニペットは、表形式を取得する方法や、データベースからの列を示します。 


```
var db = srv.Databases.GetByName("abc"); 

Column c1 = db.Model.Tables["foo"].Columns["bar"]; 
if (c1.ObjectType == ObjectType.Column) // always true 

MetadataObject obj; 

switch(obj.ObjectType) 
{ 
 case ObjectType.Table: 
  var t1 = (Table)obj; 
  break; 
} 
```

## <a name="next-steps"></a>次の手順

理解する方法[作成し、空のデータベースを展開](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-and-deploy-an-empty-database-analysis-services-amo-tom.md)TOM API を使用しています。

