---
title: "SQL Server にインストールされているパッケージの確認 | Microsoft Docs"
ms.custom: ""
ms.date: "08/31/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# SQL Server にインストールされているパッケージの確認
  このトピックでは、インストールされている R パッケージを特定する方法について説明します [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス。  
  
既定では、インストールの [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 各インスタンスに関連付けられている R パッケージ ライブラリを作成します。 そのため、コンピューターにインストールされているパッケージを理解する R サービスがインストールされている各インスタンスにこのクエリを実行する必要があります。 パッケージ ライブラリは **いない** インスタンス間で共有すると、実行できないことが別のインスタンスにインストールされている他のパッケージでします。

インスタンスの既定のライブラリの場所を決定する方法については、次を参照してください。 [R パッケージの管理をインストールおよび](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)です。   
   
 
## R を使用してインストールされているパッケージの一覧を取得します。  
 R ツールと R 関数を使用してインストールされているか読み込まれているパッケージの一覧を取得する複数の方法があります。  
  
+   多くの R 開発ツールでは、オブジェクト ブラウザーや、インストール済みパッケージまたは現在の R ワークスペースに読み込まれているパッケージの一覧が提供されます。  

+ パッケージの管理向けに提供されて RevoScaleR パッケージから次の関数のコンテキストを計算することをお勧めします。
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/rxfindpackage)
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/rxInstalledPackages)   
  
+   `installed.packages()`のような R 関数を使用できます。この関数は、インストールされている `utils` パッケージに含まれています。 この関数は、パッケージごとに、指定したライブラリが見つかり、パッケージ名、ライブラリ パス、およびバージョン番号のマトリックスを返すの説明ファイルをスキャンします。  
 
### 使用例  
次の例は、関数を使用して `rxInstalledPackages` 提供されている SQL Server の計算コンテキストで使用可能なパッケージの一覧を取得します。

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 次の例は、基本の R 関数を使用して `installed.packages()` で、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを現在のインスタンスの R_SERVICES ライブラリにインストールされているパッケージの行列を取得します。 DESCRIPTION ファイル内のフィールドが解析されないようにするために、名前のみが返されます。  
  
```  
EXECUTE sp_execute_external_script  
@language=N'R'  
,@script = N'str(OutputDataSet);  
packagematrix <- installed.packages();  
NameOnly <- packagematrix[,1];  
OutputDataSet <- as.data.frame(NameOnly);'  
,@input_data_1 = N'SELECT 1 as col'  
WITH RESULT SETS ((PackageName nvarchar(250) ))  
```  
  
 詳細については、既定値と省略可能なフィールド、R パッケージの説明ファイルで、次を参照してください。 [https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file](https://cran.r-project.org/doc/manuals/R-exts.html)します。  
  
## 参照  
 [SQL Server に追加の R パッケージをインストールする](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  