---
title: "SQL Server と共にインストールされている R パッケージ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 4d426cf6-a658-4d9d-bfca-4cdfc8f1567f
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 082aea3b1cde3c335dd7fa51b8ef219fc30f7efd
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="r-packages-installed-with-sql-server"></a>SQL Server と共にインストールされている R パッケージ
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、インストールし、マシン学習機能を有効にする場合は、SQL Server と一緒にインストールされている R パッケージについて説明します。 この記事では、管理し、既存のパッケージを表示または SQL Server インスタンスに新しいパッケージを追加する方法も説明します。

**適用されます:** SQL Server 2017 Machine Learning Services (In-database)、SQL Server 2016 R Services (In-database)

## <a name="what-is-the-instance-library-and-where-is-it"></a>インスタンスのライブラリおよび場所とは

SQL Server で実行されている任意の R ソリューションでは、インスタンスに関連付けられている既定の R ライブラリにインストールされているパッケージのみを使用できます。 SQL Server で R の機能をインストールするときに、R パッケージのライブラリは、インスタンス フォルダーに格納します。

+ 既定のインスタンス*MSSQLSERVER* 

    SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library` 
    
    SQL Server 2016: `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`

+ 名前付きインスタンス*MyNamedInstance* 

    SQL Server 2017: `C:\Program Files\Microsoft SQL Server\MSSQL14.MyNamedInstance\R_SERVICES\library` 
    
    SQL Server 2016: `C:\Program Files\Microsoft SQL Server\MSSQL13.MyNamedInstance\R_SERVICES\library`

次のステートメントを実行すると、R の現在のインスタンスの既定のライブラリを確認することができます。

```sql
EXECUTE sp_execute_external_script  @language = N'R'
, @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

また、使用できます、新しい[rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) sp を実行している場合に、機能\_実行\_外部\_ターゲット コンピューター上で直接スクリプト。 関数は、リモート接続のライブラリ パスを返すことはできません。

```sql
EXEC sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
```

> [!NOTE]
> バインディングを使用してインスタンスに R コンポーネントをアップグレードする場合、インスタンスのライブラリへのパスを変更できます。 必ず SQL Server でどのライブラリが使用されていることを確認してください。

## <a name="r-packages-installed-with-sql-server"></a>SQL Server と共にインストールされている R パッケージ

既定では、R**基本**パッケージがインストールされています。 基本パッケージを含めるなどパッケージによって提供されるコア機能`stats`と`utils`です。

常に SQL Server 2016 または SQL Server 2017 での R のインストールに含まれる、 **RevoScaleR**パッケージ、および関連する拡張パッケージおよびプロバイダー、リモート計算コンテキストをサポートするストリーミング、並列 rx 関数の実行とその他の多くの機能です。 RevoScaleR パッケージをアップグレードするには、か、機械学習のコンポーネントだけをアップグレードまたは修正プログラムまたは新しいバージョンの SQL Server のインスタンスをアップグレードするバインディングを使用します。

+ 強化された R 機能の概要については、次を参照してください[Machine Learning サーバーについて。](https://docs.microsoft.com/machine-learning-server/what-is-microsoft-r-server)

+ クライアント コンピューター上に RevoScaleR ライブラリをダウンロードするには、インストール[Microsoft R クライアント](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

## <a name="permissions-required-for-installing-r-packages"></a>R パッケージをインストールするために必要なアクセス許可

SQL Server 2016 では、管理者は、インスタンス全体を対象に新しい R パッケージをインストールする必要があります。 

SQL Server 2017 には、パッケージのインストールと管理の新機能が導入されています。

+ リモート クライアントから R コマンドを使用して、プライベートまたは共有のいずれかのスコープを使用してパッケージをインストールすることができます。 この機能では、いずれかが必要[Microsoft R Server](https://docs.microsoft.com/machine-learning-server/install/r-server-install)または[Machine Learning サーバー](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)、インスタンスに対する dbo 特権とします。
+ 新しいデータベース機能が追加されましたパッケージの管理をサポートするためにデータベース管理者によって T-SQL を使用してなし。 今後、これらの機能は、特権のあるユーザーへのパッケージ管理のほとんどのファセットを委任することを Dba を提供します。

このセクションでは、インストールし、バージョンごとのパッケージの管理に必要な権限について説明します。

+ SQL Server 2016 R Services (In-database)

    実行しているコンピューターに新しい R パッケージをインストールする[!INCLUDE [ssCurrent](..\..\includes\sscurrent-md.md)]、コンピューターに対する管理者権限を持つ必要があります。 必要なすべてのパッケージがインストールされていることを確認するには、データベース管理者またはサーバーの他の管理者のタスクは、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]インスタンス。

    ない管理者特権コンピューターでホストしている場合、 [!INCLUDE [ssNoVersion_md](..\..\includes\ssnoversion-md.md)]インスタンス、R パッケージをインストールする方法に関する管理者向けの情報を提供して、セキュリティで保護されたパッケージ リポジトリへのアクセスを提供、パッケージ化によって要求されたユーザーを取得できます。

+ SQL Server 2017 Machine Learning サービス

    SQL Server インスタンスの管理者の場合で新しいパッケージをインストールできます。 インスタンスに関連付けられている既定のライブラリを使用することを確認するだけです。 ストアド プロシージャから呼び出されたときに、他の場所にインストールされているパッケージを実行できません。 コンピューティング コンテキストとしても、SQL Server を使用して実行するすべての R コードでは、パッケージが、インスタンス ライブラリで使用できることが必要です。

    このリリースでは、今後のリリースでの Dba によってパッケージの管理が簡単をサポートすると一部の新機能も含まれます。 ここでは、インスタンス単位での R パッケージのインストールを続行することをお勧めします。

+ R Server (スタンドアロン)

    新しい R パッケージをインストールするコンピューターに対する管理者権限が必要です。

+ その他のクライアント環境

    R ワークステーションとして使用されているコンピューターに新しい R パッケージをインストールするかどうかはそのコンピューター**いない**のインスタンスがある[!INCLUDE[ssNoVersion_md](..\..\includes\ssnoversion-md.md)]をインストールする必要がありますにコンピューターに対する管理者権限パッケージをインストールします。 パッケージをインストールしたら、それをローカルで実行することができます。

## <a name="managing-or-viewing-installed-packages"></a>インストールされているパッケージの管理または表示します。

現在インストールされているパッケージの完全な一覧を取得できる複数の方法はあります。 詳細については、次を参照してください。 [SQL Server にインストールされているパッケージを決定](determine-which-packages-are-installed-on-sql-server.md)です。
