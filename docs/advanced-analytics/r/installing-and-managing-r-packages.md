---
title: "R パッケージのインストールと管理 | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ae30bfc42e42b69158dbba5a38b0bccbe93523b4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="installing-and-managing-r-packages"></a>R パッケージのインストールと管理
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で実行される R ソリューションでは、既定の R ライブラリにインストールされたパッケージを使用する必要があります。 通常、R ソリューションでは、R コード内でファイル パスを指定することでユーザーのライブラリを参照しますが、これは本番環境では推奨されません。

そのため、必要なすべてのパッケージが [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスにインストールされていることを、データベース管理者か、またはサーバー上のその他の管理者が確認する必要があります。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスをホストするコンピューターでの管理者特権が自分にない場合は、R パッケージのインストール方法に関する情報を管理者に提供し、ユーザーによって要求されたパッケージを取得できる、セキュアなパッケージ リポジトリへのアクセス権を提供することができます。 ここでは、この情報について説明します。 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] では、R パッケージのインストールと管理に関する新しい機能が提供されています。これにより、データベース管理者とデータ サイエンティストは、パッケージの使用方法や設定をより自由に制御することができます。 詳しくは、 「[R Package Management for SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)」(SQL Server の R パッケージ管理) をご覧ください。 

## <a name="installed-packages"></a>インストール済みパッケージ
[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールすると、既定では、R の**基本**パッケージがインストールされます。これには、`stats` や `utils` のほか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続をサポートする**RevoScaleR** パッケーが含まれています。  
  
 
> [!NOTE]  
>  既定でインストールされているパッケージの一覧は、「[Packages Installed with Microsoft R Open](https://mran.microsoft.com/rro/installed/)」(Microsoft R Open にインストールされているパッケージ) をご覧ください。  

 CRAN または別のリポジトリから追加のパッケージが必要な場合は、目的のパッケージをダウンロードし、ワークステーションにインストールする必要があります。  
  
 サーバーのコンテキストで新しいパッケージを実行する必要がある場合、管理者はそのパッケージもサーバーにインストールする必要があります。   
   
## <a name="where-and-how-to-get-new-packages"></a>新しいパッケージの取得場所と取得方法  
 R パッケージの供給元は複数あります。その中でもよく知られているのは CRAN と Bioconductor です。 R 言語の公式サイト ([https://www.r-project.org/](https://www.r-project.org/)) には、これらのリソースが多数掲載されています。 または、GitHub に多くのパッケージが公開されており、ここではソース コードを取得できます。 ただし、社内の誰かによって開発された R パッケージが提供されている場合もあります。  
  
 供給元に関係なく、インストールできるパッケージは ZIP ファイルの形式で提供されます。 また、パッケージを [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] で使用するには、必ず Windows バイナリ形式で ZIP ファイルを入手してください  (一部のパッケージでは、この形式がサポートされない場合もあります)。ZIP ファイル形式のコンテンツと、R パッケージの作成方法の詳細については、R プロジェクトのサイトから PDF 形式でダウンロードできる、次のチュートリアルを参照することをお勧めします: [Freidrich Leisch: Creating R Packages](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf) (R パッケージの作成)。 
  
 通常、R パッケージは事前にダウンロードしておかなくても、コンピューターがインターネットに接続されていれば、コマンドラインから簡単にインストールできます。  通常、これは [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] を実行しているサーバーについては当てはまりません。  したがって、インターネットに接続されて**いない**コンピューターに R パッケージをインストールするには、適切な ZIP 形式のパッケージを事前にダウンロードし、その ZIP ファイルを、コンピューターからアクセスできるフォルダーにコピーする必要があります。 
 
 以下のトピックでは、パッケージをオフラインでインストールするための 2 つの方法について説明しています。 

+ [Create an Offline Package Repository using miniCRAN](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md) (miniCRAN を使用してオフライン パッケージ リポジトリを作成する)

  R パッケージ **miniCRAN** を使用してオフライン リポジトリを作成する方法について説明します。 パッケージを複数のサーバーにインストールし、1 つの場所からリポジトリを管理する必要がある場合は、通常、これが最も効率的な方法です。 
+ [Install New R Packages from the Internet](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md) (インターネットから新しい R パッケージをインストールする)

  ZIP ファイルを手動でコピーして、パッケージをオフラインでインストールする手順が説明されています。   

## <a name="permissions-required-for-installing-r-packages"></a>R パッケージをインストールする上で必要なアクセス許可  
  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を実行しているコンピューターに新しい R パッケージをインストールするには、そのコンピューターに対する管理者権限を持つ必要があります。   

これらの権限がない場合は、管理者に連絡し、インストールするパッケージに関する情報を渡してください。  
  

R ワークステーションとして使用されるコンピューターに新しい R パッケージをインストールする場合、そのコンピューターに [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] のインスタンスがインストールされて**いなくても**、パッケージをインストールするコンピューターに対する管理者権限が必要です。 パッケージをインストールしたら、それをローカルで実行することができます。  
 
> [!NOTE]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] では、パッケージのインストール権限をインスタンス レベルとデータベース レベルでスコープ設定できる、新しいデータベース ロールが追加されました。 詳しくは、 「[R Package Management for SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)」(SQL Server の R パッケージ管理) をご覧ください。
 

### <a name="location-of-default-r-library-location-for-r-services"></a>R Services の既定の R ライブラリの場所

既定のインスタンスを使用して [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] をインストールした場合、そのインスタンスによって使用される R パッケージ ライブラリは、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスのフォルダーに配置されます。 例: 

+ 既定インスタンス _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ 名前付きインスタンス _MyNamedInstance_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


次のステートメントを実行すると、R の現在のインスタンスの既定のライブラリを確認することができます。 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

詳しくは、「[Determine Which Packages are Installed on SQL Server](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md)」(SQL Server にインストールされているパッケージの確認) をご覧ください。

## <a name="managing-installed-packages"></a>インストール済みパッケージの管理

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] では、R パッケージのインストールと管理に関する新しい機能が提供されています。これにより、データベース管理者とデータ サイエンティストは、パッケージの使用方法や設定をより自由に制御することができます。 詳しくは、 「[R Package Management for SQL Server](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)」(SQL Server の R パッケージ管理) をご覧ください。 

SQL Server 2106 R Services を使用している場合、新しいパッケージ管理機能は現時点では使用できません。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターにインストールされているパッケージを確認するには、次のいずれかのオプションを使用してください。

+ 既定のライブラリを表示する (フォルダーへのアクセス許可がある場合)。
+ R コマンドからコマンドを実行して、R_SERVICES ライブラリの場所にあるパッケージを一覧表示する
+ インスタンスで、次のようなストアド プロシージャを使用する。
   ```SQL
   EXECUTE sp_execute_external_script  @language=N'R'  
        ,@script = N'str(OutputDataSet);  
        packagematrix <- installed.packages();  
        NameOnly <- packagematrix[,1];  
        OutputDataSet <- as.data.frame(NameOnly);'  
        ,@input_data_1 = N'SELECT 1 as col'  
        WITH RESULT SETS ((PackageName nvarchar(250) ))   
   ```


 ## <a name="see-also"></a>参照  
 [Managing and Monitoring R Solutions](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md) (R ソリューションの管理と監視)  

