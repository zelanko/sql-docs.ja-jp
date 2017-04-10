---
title: "データ サイエンスのチュートリアルの前提条件 (SQL Server R Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: 12
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 12
---
# データ サイエンスのチュートリアルの前提条件 (SQL Server R Services)
同じネットワーク上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンピューターに接続できる R ワークステーションでチュートリアルを実行することをお勧めします [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と R 開発環境の両方を備えたコンピューターでこのチュートリアルを実行することもできます。 
  
  
## <a name="install-sql-server-2016-r-services-in-database"></a>SQL Server 2016 R Services (In-Database) をインストールする  
[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  がインストールされている [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のインスタンスにアクセスできる必要があります。 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]のセットアップ方法について詳しくは、「 [SQL Server R Services (In-Database) をセットアップする](https://msdn.microsoft.com/library/mt696069.aspx)」を参照してください。  
  
  
> [!IMPORTANT]  
> 必ず、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 以降を使用してください。 それより前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では R との統合がサポートされていません。ただし、ODBC データ ソースとして以前の SQL データベースを使用することはできます。  
  
## <a name="install-an-r-development-environment"></a>R 開発環境をインストールする  
コンピューターでこのチュートリアルを実行するには、R 開発環境または R コマンドを実行できる他のコマンド ライン ツールが必要です。    
  
- **R Tools for Visual Studio** は、Intellisense、デバッグ、および Microsoft R Server と SQL Server R Services のサポートを提供する無料プラグインです。 ダウンロードするには、「 [R Tools for Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx)」を参照してください。  
    
- **Microsoft R Client** は、ScaleR パッケージを使用する R での開発をサポートする軽量の開発ツールです。 これを取得する方法については、「[Get Started with Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started)」 (Microsoft R Client の概要) を参照してください。
  
- **RStudio** は R 開発用の最も一般的な環境の 1 つです。 詳しくは、 [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/)参照してください。  
  
    ただし、RStudio または他の環境の汎用インストールではこのチュートリアルを実行できません。また、R パッケージおよび Microsoft R Open の接続ライブラリをインストールする必要があります。 詳しくは、「 [データ サイエンス クライアントのセットアップ](https://msdn.microsoft.com/library/mt696067.aspx)」を参照してください。  

- [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)] をインストールすると、R ツール (R.exe、RTerm.exe、RScripts.exe) が既定でインストールされます。 IDE をインストールしたくない場合は、これらのツールを使用できます。  
  
  
## <a name="get-permissions-to-connect-to-sql-server"></a>SQL Server に接続するアクセス許可を取得する  
このチュートリアルでは、スクリプトを実行してデータをアップロードするために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。 そのためには、データベース サーバーでの有効なログインが必要です。  SQL ログインまたは統合 Windows 認証を使用できます。 データベース管理者に、R を使用するデータベースに対する以下の特権を持つアカウントをサーバーに作成してもらってください。  
  
-   データベース、テーブル、関数、ストアド プロシージャの作成    
-   テーブルへのデータの挿入  
  
  
## <a name="start-the-walkthrough"></a>チュートリアルの開始  
[レッスン 1: データを準備する (データ サイエンスのエンド ツー エンド チュートリアル)](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
  
  
