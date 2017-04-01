---
title: "インストールして、R パッケージを管理します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# インストールして、R パッケージを管理します。
 実行される R ソリューション [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] R の既定のライブラリにインストールされているパッケージを使用する必要があります。 通常は、R ソリューションは、R コードでファイルのパスを指定することによってユーザーのライブラリが参照されますが、実稼働これは推奨されません。

したがってに必要なすべてのパッケージがインストールされていることを確認するには、データベース管理者またはその他のサーバーの管理者のタスクが、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンス。 かどうか必要はありません管理者特権でコンピューターをホストする、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]  インスタンスを提供する R パッケージをインストールする方法に関する管理者の情報へとユーザーによって要求されたパッケージを取得できるセキュリティで保護されたパッケージ リポジトリへのアクセスを提供します。 このセクションでは、その情報を提供します。 

> [!TIP]
> [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] インストールして、データベース管理者とデータ サイエンティストをより自由とパッケージの使用状況とセットアップに制御を提供する R パッケージの管理の新機能を提供します。 詳細については、次を参照してください。 [R パッケージの管理 SQL Server の](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)です。 

## <a name="installed-packages"></a>インストールされているパッケージ
インストールするときに  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)],  、既定では、R **基本** など、パッケージがインストールされる `stats` と `utils`, と共に、 **RevoScaleR** への接続をサポートするパッケージを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 
> [!NOTE]  
>  既定でインストールされているパッケージの一覧は、次を参照してください。 [Microsoft R Open とパッケージがインストールされている](https://mran.microsoft.com/rro/installed/)します。  

 CRAN または別のリポジトリからパッケージを追加する場合は、パッケージをダウンロードし、ワークステーションにインストールする必要があります。  
  
 サーバーのコンテキストで新しいパッケージを実行する必要がある場合、管理者必要がありますサーバーにインストールもします。   
   
## <a name="where-and-how-to-get-new-packages"></a>新しいパッケージの取得場所と取得方法  
 R パッケージの供給元は複数あります。その中でもよく知られているのは CRAN と Bioconductor です。 R 言語の公式サイト ([https://www.r-project.org/](https://www.r-project.org/)) これらのリソースの多くを一覧表示します。 または、GitHub に多くのパッケージが公開されており、ここではソース コードを取得できます。 ただし、社内の誰かによって開発された R パッケージが提供されている場合もあります。  
  
 供給元に関係なく、インストールできるパッケージは ZIP ファイルの形式で提供されます。 さらに、使用してパッケージを使用する [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], 、Windows バイナリ形式では、zip 形式のファイルを入手してください。 (一部のパッケージは、この形式をサポートがされません)。R パッケージを作成する方法と、zip ファイル形式の内容に関する詳細については、このチュートリアルでは、R プロジェクトのサイトから PDF 形式でダウンロードできますお勧めします。 [Freidrich Leisch: R パッケージを作成する](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf)です。 
  
 一般に、R パッケージからインストールできます簡単にコマンド ラインに事前にダウンロードすることがなくコンピュータがインターネットにアクセスします。  一般にこの該当しない場合は、実行しているサーバーで [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] します。  そのためがコンピューターに R パッケージをインストールする **いない** インターネットにアクセス、前もって正しい (zip 形式) 形式でパッケージをダウンロードし、コンピューターからアクセスできるフォルダーに zip ファイルをコピーする必要があります。 
 
 次のトピックでは、オフライン パッケージをインストールするための 2 つの方法について説明します。 

+ [オフライン パッケージのリポジトリを作成 miniCRAN を使用します。](../../advanced-analytics/r-services/create-a-local-package-repository-using-minicran.md)

  R パッケージを使用する方法について説明 **miniCRAN** オフライン リポジトリを作成します。 これは、複数のサーバーにパッケージをインストールし、1 つの場所からリポジトリを管理する必要がある場合、最も効率的な方法では可能性があります。 
+ [インターネットからの新しい R パッケージをインストールします。](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)

  Zip ファイルを手動でコピーしてオフライン パッケージをインストールする手順が含まれます。   

## <a name="permissions-required-for-installing-r-packages"></a>R パッケージをインストールする上で必要なアクセス許可  
  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]を実行しているコンピューターに新しい R パッケージをインストールするには、そのコンピューターに対する管理者権限を持つ必要があります。   

これらの権限がない場合は、管理者に連絡し、インストールするパッケージに関する情報を渡してください。  
  

R ワークステーションとして使用されているコンピューターに新しい R パッケージをインストールするかどうか、およびでは、コンピュータ **いない** のインスタンスがある [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] をインストールする必要があります、パッケージをインストールするコンピューターに管理者権限。 パッケージをインストールしたら、それをローカルで実行することができます。  
 
> [!NOTE]
>  [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], 、インスタンス レベルおよびデータベース レベルでのパッケージのインストールのアクセス許可のスコープの設定をサポートする新しいデータベース ロールが追加されました。 詳細については、次を参照してください。 [R パッケージの管理 SQL Server の](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)です。
 

### <a name="location-of-default-r-library-location-for-r-services"></a>R のサービスの既定 R ライブラリの場所の場所

インストールした場合  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 既定のインスタンスを使用して、インスタンスによって使用される R パッケージ ライブラリは、下にある、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスのフォルダーです。 例: 

+ 既定のインスタンス _MSSQLSERVER_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
+ 名前付きインスタンス _MyNamedInstance_
  `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library` 


R です。 現在のインスタンスの既定のライブラリを確認するには、次のステートメントを実行することができます。 
~~~~
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
~~~~

詳細については、次を参照してください。 [を決定するパッケージが SQL Server にインストールされている](../../advanced-analytics/r-services/determine-which-packages-are-installed-on-sql-server.md)します。

## <a name="managing-installed-packages"></a>インストール済みパッケージの管理

[!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] インストールして、データベース管理者とデータ サイエンティストをより自由とパッケージの使用状況とセットアップに制御を提供する R パッケージの管理の新機能を提供します。 詳細については、次を参照してください。 [R パッケージの管理 SQL Server の](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)です。 

SQL Server 2106 R サービスを使用している場合、新しいパッケージの管理に関する機能はこの時点で使用できません。 その間は、インストールされているパッケージを決定するため、これらのオプションがある、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターでこれらのオプションのいずれか。

+ フォルダーへのアクセス許可がある場合は、既定のライブラリを表示します。
+ R_SERVICES ライブラリの場所にパッケージを一覧表示する R コマンドからコマンドを実行します。
+ インスタンスで、次のようにストアド プロシージャを使用します。
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
 [管理と監視 R ソリューション](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  