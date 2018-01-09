---
title: "有効にするにまたは SQL Server の R パッケージの管理を無効にする |Microsoft ドキュメント"
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
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 3c3dab54416d680e0d021a2edf9fbe33d5a0d81f
ms.sourcegitcommit: 60d0c9415630094a49d4ca9e4e18c3faa694f034
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="enable-or-disable-r-package-management-for-sql-server"></a>有効にするにまたは SQL Server の R パッケージの管理を無効にします。

この記事は、データベース管理者は R. ではなく、T-SQL を使用して、インスタンス上のパッケージのインストールを制御できるように設計された、SQL Server 2017 で新しいパッケージ管理機能をについて説明します

パッケージ管理 frature が有効になっている ater、リモート クライアントにデータベース参照を返しますにパッケージをインストールするのに R コマンドを使用することができますも。

> [!NOTE]
> 既定では、SQL Server の外部のパッケージ管理機能は無効、マシン学習機能がインストールされている場合でもです。 

## <a name="enable-package-management"></a>パッケージの管理を有効にします。

[を有効にする](#bkmk_enable)この機能は、データベース管理者を必要とする、2 段階のプロセス。

1.  SQL Server インスタンス (SQL Server インスタンスごと) のパッケージ管理を有効にする

2.  SQL Database (SQL Server データベースごと) のパッケージ管理を有効にする

[を無効にする](#bkmk_disable)パッケージ管理機能では、データベース レベルのパッケージと、アクセス許可を削除するプロセスを反転し、サーバーから役割を削除します。

1.  各データベース (データベースごと) のパッケージ管理を無効にする

2.  SQL Server インスタンス (インスタンスごと) のパッケージ管理を無効にする

## <a name="bkmk_enable"></a>パッケージの管理を有効にします。

を有効にするにまたはパッケージの管理を無効にするには、コマンド ライン ユーティリティを使用して**RegisterRExt.exe**、に含まれている、 **RevoScaleR**パッケージです。

1. 管理者特権のコマンド プロンプトを開き、ユーティリティ、RegisterRExt.exe を含むフォルダーに移動します。 既定の場所は`<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`します。

2. 環境内の適切な引数を指定して、次のコマンドを実行します。

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、パッケージの管理に必要な SQL Server コンピューターのインスタンス レベルのオブジェクトを作成します。 また、インスタンスのスタート パッドを再起動します。

    インスタンスを指定しないと、既定のインスタンスが使用されます。 ユーザーを指定しないと、現在のセキュリティ コンテキストが使用されます。 たとえば、次のコマンドは、RegisterRExt.exe をコマンド プロンプトを開いたユーザーの資格情報のパスでインスタンスにパッケージの管理を有効します。

    `REgisterRExt.exe /installpkgmgmt`

2.  特定のデータベースにパッケージの管理を追加するには、管理者特権でコマンド プロンプトから次のコマンドを実行します。

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    このコマンドは、ユーザーのアクセス許可を制御するために使用される次のデータベース ロールを含む一部のデータベース アイテムを作成します。 `rpkgs-users`、 `rpkgs-private`、および`rpkgs-shared`です。

    たとえば、次のコマンドは、RegisterRExt を実行しているインスタンス上のデータベース、パッケージの管理を使用できます。 ユーザーを指定しないと、現在のセキュリティ コンテキストが使用されます。 

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

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

4.  機能が有効にすると、サーバーへの接続しインストールしたりするパッケージをリモートで同期 R コマンドを使用します。 このしくみの例は、次を参照してください。 [SQL Server のその他のパッケージをインストール](install-additional-r-packages-on-sql-server.md)です。

## <a name="bkmk_disable"></a>パッケージの管理を無効にします。

1.  管理者特権でコマンド プロンプトから RegisterRExt ユーティリティを再実行し、データベース レベルでのパッケージの管理を無効にします。

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、指定されたデータベースからパッケージの管理に関連するデータベース オブジェクトを削除します。 SQL Server コンピューターのセキュリティで保護されたファイル システムの場所からインストールされたすべてのパッケージも削除されます。

2. パッケージの管理が使用されたデータベースごとに 1 回、このコマンドを実行します。 

3.  (省略可能)前の手順を使用してパッケージのすべてのデータベースが消去された後は、管理者特権でコマンド プロンプトから次のコマンドを実行します。

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、インスタンスからパッケージの管理機能を削除します。 変更を確認するには、もう一度、スタート パッド サービスを手動で再起動する必要があります。

## <a name="see-also"></a>参照

[SQL Server の R パッケージの管理](r-package-management-for-sql-server-r-services.md)
