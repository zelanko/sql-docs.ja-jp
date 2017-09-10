---
title: "miniCRAN を使用してローカル パッケージ リポジトリを作成する | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27f2a1ce-316f-4347-b206-8a1b9eebe90b
caps.latest.revision: 4
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e8af93b3e132290eef4b43da568b9381ff8e5a04
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-local-package-repository-using-minicran"></a>miniCRAN を使用してローカル パッケージ リポジトリを作成する
このトピックでは、R パッケージ **miniCRAN** を使用して、ローカルの R パッケージ リポジトリを作成する方法について説明します。 

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスは、通常はインターネット接続がないサーバーに配置されるため、R パッケージをインストールする標準的な方法 (R コマンド `install.packages()`) は機能しません。これは、パッケージ インストーラーが CRAN またはその他のミラー サイトにアクセスできないためです。

ローカル共有またはリポジトリからパッケージをインストールするためのオプションは 2 つあります。

+ miniCRAN パッケージを使用して、必要なパッケージのローカル リポジトリを作成し、そのリポジトリからインストールします。 このトピックでは、この miniCRAN を使用する方法について説明します。

+ 必要なパッケージとそれらに依存するものを zip ファイルとしてダウンロードし、ローカル フォルダーに保存します。次に、そのフォルダーを [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターにコピーします。 この手動コピーによる方法の詳細については、「[Install Additional R Packages on SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md)」(追加 R パッケージを SQL Server にインストールする) をご覧ください。


## <a name="step-1-install-minicran-and-download-packages"></a>手順 1. miniCRAN をインストールしてパッケージをダウンロードする 


1. インターネットにアクセスできるコンピューターに miniCRAN パッケージをインストールします。

   ~~~~
   # Install miniCRAN and igraph

   if(!require("miniCRAN")) install.packages("miniCRAN")
   if(!require("igraph")) install.packages("igraph")
   library(miniCRAN)

   # Define the package source: a CRAN mirror, or an MRAN snapshot
   CRAN_mirror <- c(CRAN = "https://mran.microsoft.com/snapshot/2016-04-01")

   # Define the local download location
   local_repo <- "~/miniCRAN"
   ~~~~

2. 次の R スクリプトを使用して、必要なパッケージをそのコンピューターにダウンロードするかインストールします。 これにより、後でパッケージを [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] にコピーするために必要なフォルダー構造が作成されます。

   ~~~~
   # List the packages to get. Do not specify dependencies.
   pkgs_needed <- c("ggplot2", "ggdendro")
   # Plot the dependency graph 
   plot(makeDepGraph(pkgs_needed)) 
   
   # Create the local repo 
   pkgs_expanded <- pkgDep(pkgs_needed, repos = CRAN_mirror) 
   makeRepo(pkgs_expanded, path = local_repo, repos = CRAN_mirror, type = "win.binary", Rversion = "3.2") 

   # List local packages 
   pdb <- as.data.frame( 
     pkgAvail(local_repo, type = "win.binary", Rversion = "3.2"),  
     stringsAsFactors = FALSE) 
   head(pdb) 
   pdb$Package 
   pdb[, c("Package", "Version", "License")] 
   ~~~~


## <a name="step-2-copy-the-minicran-repository-to-the-sql-server-computer"></a>手順 2. miniCRAN リポジトリを SQL Server コンピューターにコピーする 

miniCRAN リポジトリを、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] インスタンスの R_SERVICES ライブラリにコピーします。

+ SQL Server 2016 では、既定のフォルダーは `C:/Program Files/Microsoft SQL Server/MSSQL13.MSSQLSERVER/R_SERVICES/library1` です。
+ SQL Server 2017、既定のフォルダーは`C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library1`します。

R Services を名前付きインスタンスを使用してインストールしている場合は、ライブラリが適切なインスタンスにインストールされるように、パスにインスタンス名が含まれていることを確認します。 たとえば、名前付きインスタンスが RTEST02 の場合、この名前付きインスタンスの既定のパスは `C:\Program Files\Microsoft SQL Server\MSSQL13.RTEST02\R_SERVICES\library` になります。

SQL Server を別のドライブにインストールしていたり、インストール パスにその他の変更を加えたりしている場合は、それらの変更もパスに反映するようにします。

## <a name="step-3-install-the-packages-on-sql-server-using-the-minicran-repository"></a>手順 3. miniCRAN リポジトリを使用して SQL Server にパッケージをインストールする

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] コンピューターで、管理者として R コマンドラインまたは RGUI を開きます。 
  
> [!TIP]
> コンピューターに複数の R ライブラリが存在することがあります。このため、パッケージを適切なインスタンスに確実にインストールするには、パッケージのインストール先となるインスタンスと一緒にインストールされている RGUI または RTerm のコピーを使用します。
  
リポジトリの指定を求めるメッセージが表示されたら、コピーしたばかりのファイルを含むフォルダー (ローカル miniCRAN リポジトリ) を選択します。

   ~~~~
   # Run this R code as administrator on the SQL Server computer 
   pkgs_needed <- c("ggplot2", "ggdendro") 
   local_repo  <- "~/miniCRAN" 

   # OPTIONAL: If you are not running R from the instance library as recommended, you must specify the path
   #   .libPaths()[1] 
   # "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER/R_SERVICES/library " 
   # lib <- .libPaths()[1]
   
   install.packages(pkgs_needed,  
                    repos = file.path("file://", normalizePath(local_repo, winslash = "/")), 
                    lib = lib, 
                    type = "win.binary", 
                    dependencies = TRUE 
                    ) 
   installed.packages() 
   ~~~~

パッケージがインストールされたことを確認します。
   ~~~~
   installed.packages()
   ~~~~



## <a name="acknowledgements"></a>謝辞

この情報のソースは、Andre de Vries による記事です。同氏は miniCRAN パッケージも開発しています。 詳細と完全なチュートリアルについてはは、「[How to install R packages on an off-line SQL Server 2016 instance](http://blog.revolutionanalytics.com/2016/05/minicran-sql-server.html)」(オフライン SQL Server 2016 インスタンスに R パッケージをインストールする方法) を参照してください。

