---
title: "SQL Server にインストールされているパッケージの確認 | Microsoft Docs"
ms.custom: 
ms.date: 08/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a7f7e43-b568-406c-9434-5a2ec64ec5f5
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 90e7146bde123ca8ac8a8e6ff3e11d212fd4a35a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="determine-which-packages-are-installed-on-sql-server"></a>SQL Server にインストールされているパッケージの確認
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにインストールされている R パッケージを確認する方法について説明します。  
  
既定では、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールすると、各インスタンスに関連付けられた R パッケージのライブラリが作成されます。 このため、コンピューターにインストールされたパッケージを確認するには、R Services がインストールされている各インスタンスでこのクエリを実行する必要があります。 パッケージ ライブラリはインスタンス間で共有され**ない**ため、インスタンスごとに異なるパッケージがインストールされる可能性があることに注意します。

インスタンスの既定のライブラリの場所を確認する方法については、「[Installing and Managing R Packages](../../advanced-analytics/r-services/installing-and-managing-r-packages.md) (R パッケージのインストールと管理)」をご覧ください。   
   
 
## <a name="get-a-list-of-installed-packages-using-r"></a>インストールされているパッケージの一覧を R を使用して取得する  
 R ツールと R 関数を使用すると、複数の方法でインストールまたは読み込み済みのパッケージの一覧を取得できます。  
  
+   多くの R 開発ツールでは、オブジェクト ブラウザーや、インストール済みパッケージまたは現在の R ワークスペースに読み込まれているパッケージの一覧が提供されます。  

+ 計算コンテキストでのパッケージ管理のために特別に用意された、RevoScaleR パッケージの次の関数を使用することをお勧めします。
  - [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)
  - [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)   
  
+   `installed.packages()`のような R 関数を使用できます。この関数は、インストールされている `utils` パッケージに含まれています。 この関数は、指定されたライブラリ内で見つかった各パッケージの DESCRIPTION ファイルをスキャンし、パッケージ名、ライブラリ パス、バージョン番号の行列を返します。  
 
### <a name="examples"></a>使用例  
次の例では、`rxInstalledPackages` 関数を使用して、提供されている SQL Server の計算コンテキストで使用可能なパッケージの一覧を取得します。

~~~~
sqlServerCompute <- RxInSqlServer(connectionString = 
"Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
     sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
     sqlPackages
~~~~

 次の例では、[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャで基本の R 関数 `installed.packages()` を使用して、現在のインスタンスの R_SERVICES ライブラリにインストールされているパッケージの行列を取得します。 DESCRIPTION ファイル内のフィールドが解析されないようにするために、名前のみが返されます。  
  
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
  
 詳細については、R パッケージの DESCRIPTION ファイルのオプションと既定のフィールドに関する説明 ([https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)) をご覧ください。  
  
## <a name="see-also"></a>参照  
 [SQL Server に追加の R パッケージをインストールする](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)  
  
  

