---
title: 作成および展開の空のデータベース (Analysis Services AMO-TOM) |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a58f59c48a496fb3da12330c5fa5a89942752d5d
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="create-and-deploy-an-empty-database-analysis-services-amo-tom"></a>作成し、空のデータベース (Analysis Services AMO-TOM) の展開
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
AMO TOM の一般的なプログラミング シナリオでは、データベースと、実行時にモデルを生成します。 この記事では、データベースを作成する手順について説明します。 

テーブル ソリューションは、のデータベースと、データベースごとに 1 つのモデルがモデルの間で一対一の対応関係があります。 どちらか一方、通常指定して、エンジンが存在しないオブジェクトを推論します。 

作成して、新しいデータベースの配置は、3 部構成のタスクを示します。 

* インスタンスを作成、**データベース**オブジェクトおよび名も含め、そのプロパティを設定します。 

* 追加、**データベース**オブジェクトを**Server.Databases**コレクション。 

* 呼び出す、**更新**メソッドを**データベース**に保存するオブジェクト、**サーバー**です。 

## <a name="code-example-create-empty-database"></a>コードの例: 空のデータベースを作成します。 

```
using System; 
using Microsoft.AnalysisServices; 
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
                // Generate a new database name and use GetNewName 
                // to ensure the database name is unique. 
                // 
                string newDatabaseName = 
                    server.Databases.GetNewName("New Empty Database"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var blankDatabase = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(blankDatabase); 
                blankDatabase.Update(UpdateOptions.ExpandFull); 

                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(blankDatabase.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="next-steps"></a>次の手順 

データベースが作成されると、モデル オブジェクトを追加することができます。 

- [表形式モデルにデータ ソースを追加します。](../../analysis-services/tabular-model-programming-compatibility-level-1200/add-a-data-source-to-tabular-model-analysis-services-amo-tom.md)
- [表形式モデル内のテーブル、パーティション、および列を作成します。](../../analysis-services/tabular-model-programming-compatibility-level-1200/create-tables-partitions-and-columns-in-a-tabular-model.md)
 
