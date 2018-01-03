---
title: "有効にするにまたは SQL Server の R パッケージの管理を無効にする |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/05/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 59ab247ebdb53dbd530b3becf6e90ef45bc3a503
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="enable-or-disable-r-package-management-for-sql-server"></a>有効にするにまたは SQL Server の R パッケージの管理を無効にします。

この記事では、有効または SQL Server 2017 の新しいパッケージ管理機能を無効にするプロセスについて説明します。 この機能により、データベース管理者は、インスタンス上のパッケージのインストールを制御します。 この機能は、ユーザー、必要な R パッケージをインストールする許可を与える、他のユーザーとパッケージを共有したり、新しいデータベース ロールに依存します。

既定では、SQL Server の外部のパッケージ管理機能は無効、マシン学習機能がインストールされている場合でもです。

[を有効にする](#bkmk_enable)この機能は 2 段階のプロセスであり、データベース管理者からのいくつかのヘルプが必要です。

1.  SQL Server インスタンス (SQL Server インスタンスごと) のパッケージ管理を有効にする

2.  SQL Database (SQL Server データベースごと) のパッケージ管理を有効にする

[を無効にする](#bkmk_disable)パッケージ管理機能では、データベース レベルのパッケージと、アクセス許可を削除するプロセスを反転し、サーバーから役割を削除します。

1.  各データベース (データベースごと) のパッケージ管理を無効にする

2.  SQL Server インスタンス (インスタンスごと) のパッケージ管理を無効にする

## <a name="bkmk_enable"></a>パッケージの管理を有効にします。

有効にするにまたはパッケージの管理を無効にする必要があります、コマンド ライン ユーティリティ**RegisterRExt.exe**に含まれている、 **RevoScaleR**パッケージです。

1. 管理者特権のコマンド プロンプトを開き、ユーティリティ、RegisterRExt.exe を含むフォルダーに移動します。 既定の場所は`<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`します。

2. 環境内の適切な引数を指定して、次のコマンドを実行します。

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、パッケージの管理に必要な SQL Server コンピューターのインスタンス レベルのオブジェクトを作成します。 また、インスタンスのスタート パッドを再起動します。

    インスタンスを指定しないと、既定のインスタンスが使用されます。

    ユーザーを指定しないと、現在のセキュリティ コンテキストが使用されます。

2.  データベース レベルでは、パッケージの管理を追加するには、管理者特権でコマンド プロンプトから、次のコマンドを実行します。

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    このコマンドは、ユーザーのアクセス許可を制御するために使用される次のデータベース ロールを含む一部のデータベース アイテムを作成します。 `rpkgs-users`、 `rpkgs-private`、および`rpkgs-shared`です。

    ユーザーを指定しないと、現在のセキュリティ コンテキストが使用されます。

3. パッケージをインストールする必要がありますデータベースごとに、コマンドを繰り返します。

4.  新しいロールが正常に作成されたことを確認するには、SQL Server Management Studio でデータベースをクリックして、展開**セキュリティ**、展開と**データベース ロール**です。

    Sys.database_principals、次のようにクエリを実行することもできます。

    ```SQL
    SELECT pr.principal_id, pr.name, pr.type_desc,   
        pr.authentication_type_desc, pe.state_desc,   
        pe.permission_name, s.name + '.' + o.name AS ObjectName  
    FROM sys.database_principals AS pr  
    JOIN sys.database_permissions AS pe  
        ON pe.grantee_principal_id = pr.principal_id  
    JOIN sys.objects AS o  
        ON pe.major_id = o.object_id  
    JOIN sys.schemas AS s  
        ON o.schema_id = s.schema_id;
    ```

4.  適切なアクセス許可を持つユーザーを使用できる機能が有効にすると、[外部ライブラリの作成](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql)パッケージに追加するには、t-sql ステートメントです。 このしくみの例は、次を参照してください。 [SQL Server のその他のパッケージをインストール](install-additional-r-packages-on-sql-server.md)です。

## <a name="bkmk_disable"></a>パッケージの管理を無効にします。

1.  管理者特権のコマンド プロンプトから、次のコマンドを実行し、データベース レベルでパッケージ管理を無効にします。

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    パッケージの管理が使用されたデータベースごとに 1 回、このコマンドを実行します。 このコマンドは、指定されたデータベースからパッケージの管理に関連するデータベース オブジェクトが削除されます。 SQL Server コンピューターのセキュリティで保護されたファイル システムの場所からインストールされたすべてのパッケージも削除されます。

2.  (省略可能)前の手順を使用してパッケージのすべてのデータベースが消去された後は、管理者特権でコマンド プロンプトから次のコマンドを実行します。

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、インスタンスからパッケージの管理機能を削除します。

## <a name="see-also"></a>参照

[SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)
