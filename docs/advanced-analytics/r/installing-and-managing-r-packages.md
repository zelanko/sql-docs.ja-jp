---
title: "SQL Server と共にインストールされている R パッケージ |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/29/2017
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
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 29122bdf543e82c1f429cf401b5fe1d8383515fc
ms.openlocfilehash: 0e96334850554ab642e3372c3631f3ab672109d6
ms.contentlocale: ja-jp
ms.lasthandoff: 10/10/2017

---
# <a name="r-packages-installed-with-sql-server"></a>SQL Server と共にインストールされている R パッケージ

ここでは、SQL Server と共にインストールされている R パッケージについて説明し、管理し、既存のパッケージを表示する方法に関する情報を提供します。

この記事では、SQL Server で使用する新しいパッケージを追加する方法についての情報へのリンクも提供します。

**適用されます:** SQL Server 2017 Machine Learning Services (In-database)、SQL Server 2016 R Services (In-database)

## <a name="what-is-the-instance-library-and-where-is-it"></a>インスタンスのライブラリおよび場所とは

SQL Server で実行されている任意の R ソリューションでは、インスタンスに関連付けられている既定の R ライブラリにインストールされているパッケージのみを使用できます。

SQL Server で R の機能をインストールするときに、R パッケージのライブラリは、インスタンス フォルダーに格納します。

+ 既定のインスタンス*MSSQLSERVER* 

    SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016 の場合:`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ 名前付きインスタンス*MyNamedInstance* 

    SQL Server 2017:`C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016 の場合:`C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

次のステートメントを実行すると、R の現在のインスタンスの既定のライブラリを確認することができます。

```SQL
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```
## <a name="r-packages-installed-with-sql-server"></a>SQL Server と共にインストールされている R パッケージ

インストールすると、R 言語で SQL Server では、既定では、R**基本**パッケージがインストールされています。 基本パッケージを含めるなどパッケージによって提供されるコア機能`stats`と`utils`です。

SQL Server 2016 および SQL Server 2017 で R のインストールにも含まれています、 **RevoScaleR**パッケージ、および関連する拡張パッケージおよびプロバイダー、リモート計算コンテキストをサポートするストリーミング、並列 rx 関数の実行とその他の多くの機能です。

+ 強化された R 機能の概要については、次を参照してください[Machine Learning サーバーについて。](https://docs.microsoft.com/r-server/what-is-microsoft-r-server)

+ クライアント コンピューター上に RevoScaleR ライブラリをダウンロードするには、インストール[Microsoft R クライアント](https://docs.microsoft.com/r-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>R パッケージをインストールするために必要なアクセス許可

SQL Server 2016 では、管理者は、インスタンス全体を対象に新しい R パッケージをインストールする必要があります。 SQL Server の 2017 で、データベース管理者を選択したユーザーにパッケージの管理を委任する権限を付与する新しいデータベース機能が追加されました。

このセクションでは、インストールし、バージョンごとのパッケージの管理に必要な権限について説明します。

+ SQL Server 2016 R Services (In-database)

    実行しているコンピューターに新しい R パッケージをインストールする[!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)]、コンピューターに対する管理者権限を持つ必要があります。 必要なすべてのパッケージがインストールされていることを確認するには、データベース管理者またはサーバーの他の管理者のタスクは、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]インスタンス。

    ない管理者特権コンピューターでホストしている場合、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]インスタンス、R パッケージをインストールする方法に関する管理者向けの情報を提供して、セキュリティで保護されたパッケージ リポジトリへのアクセスを提供、パッケージ化によって要求されたユーザーを取得できます。

+ SQL Server 2017 Machine Learning サービス

    このリリースには、データベース管理者は選択したユーザーにパッケージのインストールの権限を委任することのできるパッケージ管理機能が含まれています。 この機能が有効になっている、データベース管理者を追加する新しいパッケージのロールのいずれかを要求します。 詳細については、次を参照してください。 [for SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)です。

    SQL Server インスタンスの管理者の場合で新しいパッケージをインストールできます。 インスタンスに関連付けられている既定のライブラリを使用することを確認するだけです。 ストアド プロシージャから呼び出されたときに、他の場所にインストールされているパッケージを実行できません。 コンピューティング コンテキストとしても、SQL Server を使用して実行するすべての R コードでは、パッケージが、インスタンス ライブラリで使用できることが必要です。

+ R Server (スタンドアロン)

    新しい R パッケージをインストールするコンピューターに対する管理者権限が必要です。

+ その他のクライアント環境

    R ワークステーションとして使用されているコンピューターに新しい R パッケージをインストールするかどうかはそのコンピューター**いない**のインスタンスがある[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]をインストールする必要がありますにコンピューターに対する管理者権限パッケージをインストールします。 パッケージをインストールしたら、それをローカルで実行することができます。

## <a name="managing-or-viewing-installed-packages"></a>インストールされているパッケージの管理または表示します。

現在インストールされているパッケージの完全な一覧を取得できる複数の方法はあります。 詳細については、次を参照してください。 [SQL Server にインストールされているパッケージを決定](determine-which-packages-are-installed-on-sql-server.md)です。

