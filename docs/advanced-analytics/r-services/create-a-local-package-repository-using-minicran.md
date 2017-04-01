---
title: "ローカル リポジトリを使用してパッケージ miniCRAN を作成します。 | Microsoft Docs"
ms.custom: ""
ms.date: "05/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 4
---
# ローカル リポジトリを使用してパッケージ miniCRAN を作成します。
このトピックでは、R パッケージを使用してローカルの R パッケージのリポジトリを作成する方法について説明 **miniCRAN**します。 

 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスは、インターネット接続、R パッケージをインストールする標準的な方法がないサーバーに配置されます通常 (R コマンド `install.packages()`) に機能しない、パッケージ インストーラーは CRAN またはその他のすべてのミラー サイトにアクセスできません。

ローカルの共有またはリポジトリからパッケージをインストールするための 2 つのオプションがあります。

+ MiniCRAN パッケージを使用すると、必要な、このリポジトリからインストール パッケージのローカル リポジトリを作成できます。 このトピックでは、miniCRAN メソッドについて説明します。

+ が必要なパッケージとその依存関係、zip ファイルとしてをダウンロードしてローカルのフォルダーに保存し、そのフォルダーをコピー、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューター。 手動でのコピー方法の詳細については、次を参照してください。 [SQL Server 上のその他のパッケージをインストール](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)します。


## 手順 1. パッケージをダウンロードして miniCRAN のインストール 


1. インターネットにアクセスできるコンピューターで miniCRAN パッケージをインストールします。

   ~~~~
   # Install miniCRAN ---------------------------------------------------

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. ダウンロードまたは必要なパッケージをこのコンピューターにインストールします。 これにパッケージをコピーする必要があるフォルダー構造を作成、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 後です。

   ~~~~
   # List the packages you need 
   # Do not specify dependencies
   pkgs_needed <- c("ggplot2", "ggdendro")
   ~~~~

3. 上の R_SERVICES ライブラリに miniCRAN リポジトリをコピー、 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンス。

## 手順 2. SQL Server コンピューターにパッケージをインストールします。 

4.  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] R コマンドを実行しているコンピューター  `install.packages()`します。 と共にインストールされる R ツールの 1 つを使用することができます [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], などの一部としてコマンドを実行できますか Rgui.exe、 [!INCLUDE[tsql_md](../../includes/tsql-md.md)] ストアド プロシージャです。
5. リポジトリを指定するプロンプトで、コピーしたファイルを含むフォルダーを選択しますローカル miniCRAN リポジトリです。

   ~~~~
   pkgs_needed <- c("ggplot2", "ggdendro")
   local_repo  <- "~/miniCRAN"
   
   .libPaths()[1]
   "C:/Program Files/Microsoft SQL Server/130/R_SERVER/library"

   lib <- .libPaths()[1]

   install.packages(pkgs_needed, 
                 repos = file.path("file://", normalizePath(local_repo, winslash = "/")),
                 lib = lib,
                 type = "win.binary",
                 dependencies = TRUE
                 )
   ~~~~

6. この R コードを実行して、パッケージがインストールされていることを確認します。
   ~~~~
   installed.packages()
   ~~~~



## 受信確認

この情報のソースでは、この記事でも miniCRAN パッケージを作成した Andre de Vries です。 詳細と完全なチュートリアルでは、次を参照してください  [オフラインの SQL Server 2016 インスタンス上のパッケージの R をインストールする方法。](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)