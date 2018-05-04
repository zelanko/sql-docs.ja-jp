---
title: 表形式モデル内のテーブル、パーティション、および列を作成 |Microsoft ドキュメント
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
ms.assetid: cf0e4791-ad3b-41a8-81ce-509d4cf223f8
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3246c04b8aa995442a71ddc49a2282945c829fa6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-tables-partitions-and-columns-in-a-tabular-model"></a>表形式モデル内のテーブル、パーティション、および列を作成します。
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
表形式モデルでは、テーブルの行と列で構成されます。 行は、データの増分更新をサポートするパーティションに編成されます。 表形式のソリューションには、複数の種類によっては、データの取得先のテーブルをサポートできます。  

* 通常のテーブル、データ プロバイダーを介して、リレーショナル データ ソースからデータを生成する場所です。 

* ここでデータが「プッシュ」テーブルにプログラムによってプッシュされたテーブル。 

* 計算テーブルは、データがそのデータのモデル内の別のオブジェクトを参照する DAX 式からを取得します。  

次のコード例で、通常のテーブルを定義します。 

## <a name="required-elements"></a>必要な要素 

テーブルには、少なくとも 1 つのパーティションが必要です。 通常のテーブルには、少なくとも 1 つの列が定義されている必要があります。 

すべてのパーティションには、ソース データの元のドメインを指定する必要がありますが、ソースを設定することができますを null にします。 通常、ソースは、関連するデータベースのクエリ言語でデータのスライスを定義するクエリ式です。 

## <a name="code-example-create-a-table-column-parition"></a>コードの例: テーブル、列でパーティションを作成します。

テーブルは、テーブル クラス (Microsoft.AnalysisServices.Tabular 名前空間) で表されます。 

次の例では、通常のリレーショナル データ ソースといくつかの通常の列にリンクされている 1 つのパーティションを持つテーブルを定義します。 おもこのメッセージがサーバーに送信され、操作により、データをモデルにデータの更新をトリガーします。 これは、表形式のソリューションに、SQL Server リレーショナル データベースからデータをロードする場合、最も一般的なシナリオを表します。 


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
                    server.Databases.GetNewName("Database with a Table Definition"); 
 
                // 
                // Instantiate a new  
                // Microsoft.AnalysisServices.Tabular.Database object. 
                // 
                var dbWithTable = new Database() 
                { 
                    Name = newDatabaseName, 
                    ID = newDatabaseName, 
                    CompatibilityLevel = 1200, 
                    StorageEngineUsed = StorageEngineUsed.TabularMetadata, 
                }; 
 
                // 
                // Add a Microsoft.AnalysisServices.Tabular.Model object to the 
                // database, which acts as a root for all other Tabular metadata objects. 
                // 
                dbWithTable.Model = new Model() 
                { 
                    Name = "Tabular Data Model", 
                    Description = "A Tabular data model at the 1200 compatibility level." 
                }; 
 
                // 
                // Add a Microsoft.AnalysisServices.Tabular.ProviderDataSource object 
                // to the data Model object created in the previous step. The connection 
                // string of the data source object in this example  
                // points to an instance of the AdventureWorks2014 SQL Server database. 
                // 
                string dataSourceName = "SQL Server Data Source Example"; 
                dbWithTable.Model.DataSources.Add(new ProviderDataSource() 
                { 
                    Name = dataSourceName, 
                    Description = "A data source definition that uses explicit Windows credentials for authentication against SQL Server.", 
                    ConnectionString = "Provider=SQLNCLI11;Data Source=localhost;Initial Catalog=AdventureWorks2014;Integrated Security=SSPI;Persist Security Info=false", 
                    ImpersonationMode = Microsoft.AnalysisServices.Tabular.ImpersonationMode.ImpersonateAccount, 
                    Account = @".\Administrator", 
                    Password = "P@ssw0rd", 
                }); 
 
                //  
                // Add a table called Individual Customers to the data model 
                // with a partition that points to a [Sales].[vIndividualCustomer] view 
                // in the underlying data source. 
                // 
                dbWithTable.Model.Tables.Add(new Table() 
                { 
                    Name = dbWithTable.Model.Tables.GetNewName("Individual Customers"), 
                    Description = "Individual customers (names and email addresses) that purchase Adventure Works Cycles products online.", 
                    Partitions = { 
                        // 
                        // Create a single partition with a QueryPartitionSource for a query 
                        // that imports all customer rows from the underlying data source. 
                        // 
                        new Partition() { 
                            Name = "All Customers", 
                            Source = new QueryPartitionSource() { 
                                DataSource = dbWithTable.Model.DataSources[dataSourceName], 
                                Query = @"SELECT   [FirstName] 
                                                    ,[MiddleName] 
                                                    ,[LastName] 
                                                    ,[PhoneNumber]  
                                                    ,[EmailAddress] 
                                                    ,[City] 
                                        FROM [Sales].[vIndividualCustomer]", 
                            } 
                        } 
                    }, 
                    Columns = 
                    { 
                        // 
                       // DataColumn objects refer to regular table columns.  
                        // Each DataColumn object corresponds to a column in the underlying data source query. 
                        // 
                        new DataColumn() { 
                            Name = "FirstName", 
                            DataType = DataType.String, 
                            SourceColumn = "FirstName", 
                        }, 
                        new DataColumn() { 
                            Name = "MiddleName", 
                            DataType = DataType.String, 
                            SourceColumn = "MiddleName", 
                        }, 
                        new DataColumn() { 
                            Name = "LastName", 
                            DataType = DataType.String, 
                            SourceColumn = "LastName", 
                        }, 
                        new DataColumn() { 
                            Name = "PhoneNumber", 
                            DataType = DataType.String, 
                            SourceColumn = "PhoneNumber", 
                        }, 
                        new DataColumn() { 
                            Name = "EmailAddress", 
                            DataType = DataType.String, 
                            SourceColumn = "EmailAddress", 
                        }, 
                        new DataColumn() { 
                            Name = "City", 
                            DataType = DataType.String, 
                            SourceColumn = "City", 
                        }, 
                    } 
                }); 
 
                // 
                // Add the new database object to the server's  
                // Databases connection and submit the changes 
                // with full expansion to the server. 
                // 
                server.Databases.Add(dbWithTable); 
 
                //  
                // Request a full refresh to import the data from the data source and 
                // and perform any necessary recalculations. 
                // The refresh operation will be performed with the next 
                // invocation of Model.SaveChanges() or Database.Update(UpdateOptions.ExpandFull). 
                dbWithTable.Model.RequestRefresh(Microsoft.AnalysisServices.Tabular.RefreshType.Full); 
                dbWithTable.Update(UpdateOptions.ExpandFull); 
 
 
                Console.Write("Database "); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                Console.Write(dbWithTable.Name); 
                Console.ResetColor(); 
                Console.WriteLine(" created successfully."); 
 
                Console.WriteLine("The data model includes the following table definitions:"); 
                Console.ForegroundColor = ConsoleColor.Yellow; 
                foreach (Table tbl in dbWithTable.Model.Tables) 
                { 
                    Console.WriteLine("\tTable name:\t\t{0}", tbl.Name); 
                    Console.WriteLine("\ttbl description:\t{0}", tbl.Description); 
                } 
                Console.ResetColor(); 
                Console.WriteLine(); 
            } 
            Console.WriteLine("Press Enter to close this console window."); 
            Console.ReadLine(); 
        } 
    } 
} 
```

## <a name="partitions-in-a-table"></a>テーブルのパーティション 

パーティションがによって表される、**パーティション**クラス (Microsoft.AnalysisServices.Tabular 名前空間)。 **パーティション**クラスが公開する**ソース**P のプロパティ**artitionSource**にデータの取り込みの別の方法で抽象化を提供する入力します。パーティション。 A**パーティション**インスタンスが持つことができます、**ソース**の一部としてサーバーにデータのチャンクを送信することによって、パーティションにデータをプッシュはことを示すプロパティは null として Analysis Services によって公開されるデータ API のプッシュ. SQL Server 2016 で**PartitionSource**クラスには、パーティションにデータをバインドする方法を表す 2 つの派生クラス: **QueryPartitionSource**と**CalculatedPartitionSource**. 

## <a name="columns-in-a-table"></a>テーブル内の列 

列がベースから派生したいくつかのクラスによって表される**列**クラス (Microsoft.AnalysisServices.Tabular 名前空間)。 

* **DataColumn** (標準テーブルの列の標準)
* **CalculatedColumn**列に対して DAX 式でサポート)
* **CalculatedTableColumn** (標準テーブルの列の計算される)
* **RowNumberColumn** (SSAS によって作成されたすべてのテーブル列の特殊な種類)。 

## <a name="row-numbers-in-a-table"></a>テーブルの行番号 

各**テーブル**、サーバー上のオブジェクトが、 **RowNumberColumn**目的のインデックス作成に使用します。 作成または明示的に追加することはできません。 列は、保存したり、オブジェクトを更新するときに自動的に作成されます。 

* **db します。SaveChanges** 

* **db します。Update(ExpandFull)** 

いずれかのメソッドを呼び出すときに、サーバーは行番号列を自動的に作成、として表示されます。 **RowNumberColumn**テーブルの列のコレクション。 

## <a name="calculated-tables"></a>計算テーブル 

計算テーブルに基づいている DAX 式を使用、モデル内の既存のデータ構造体またはアウトオブ ライン バインドからのデータの用途を変更します。 計算テーブルをプログラムで作成するには、次の操作を行います。 

* ジェネリック型を作成する**テーブル**です。 

* ソース型は、パーティションを追加して**CalculatedPartitionSource**DAX 式は、ソースの場所。 パーティションのソースは、新機能によって、また、通常のテーブルは、計算テーブルの区別です。 

サーバーに変更を保存するときに、サーバーは一覧を返します、推定の**CalculatedTableColumns** (計算の計算テーブルの列はテーブルで構成されます)、テーブルの列のコレクションを使用して表示します。 

## <a name="next-steps"></a>次の手順

TOM の例外を処理するために使用されるクラスを確認します[TOM でのエラー処理。](../../analysis-services/tabular-model-programming-compatibility-level-1200/handling-errors-in-the-tom-api-analysis-services-amo-tom.md)
  
