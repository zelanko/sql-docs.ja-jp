---
title: 有効にするにまたは SQL Server のリモート パッケージの管理を無効にする |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/20/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 5b0039736102af09fe12e296c85cd57a83509a6b
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>有効にするにまたは SQL Server のリモート パッケージの管理を無効にします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、Machine Learning のサーバーのリモート インスタンスから R パッケージの管理を有効にする方法について説明します。 パッケージの管理機能が有効にすると、リモート クライアントからデータベースにパッケージをインストールするのに RevoScaleR コマンドを使用できます。

> [!NOTE]
> 現在、R ライブラリの管理がサポートされています。ロードマップでは、Python のサポートです。

既定では、SQL Server の外部のパッケージ管理機能は無効、マシン学習機能がインストールされている場合でもです。 次のセクションで説明したように、機能を有効にする別のスクリプトを実行する必要があります。

## <a name="overview-of-process-and-tools"></a>プロセスとツールの概要

を有効にするにまたはパッケージの管理を無効にするには、コマンド ライン ユーティリティを使用して**RegisterRExt.exe**、に含まれている、 **RevoScaleR**パッケージです。

[有効にする](#bkmk_enable)この機能は、データベース管理者を必要とする、2 段階のプロセス: (1 回 SQL Server インスタンスの場合)、SQL Server インスタンス上のパッケージの管理を有効にし、SQL データベース (1 回で 1 に SQL Server パッケージ管理を有効にします。データベースの場合)。

[無効にすると](#bkmk_disable)パッケージ管理機能も必要に multipel 手順: データベース レベルのパッケージと (データベース)、ごとに 1 回のアクセス許可を削除し、(1 回あたりのインスタンス) のサーバーから役割を削除します。

## <a name="bkmk_enable"></a> パッケージの管理を有効にします。

1. 管理者特権のコマンド プロンプトを開き、ユーティリティ、RegisterRExt.exe を含むフォルダーに移動します。 既定の場所は`<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`します。

2. 環境内の適切な引数を指定して、次のコマンドを実行します。

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、パッケージの管理に必要な SQL Server コンピューターのインスタンス レベルのオブジェクトを作成します。 また、インスタンスのスタート パッドを再起動します。

    インスタンスを指定しないと、既定のインスタンスが使用されます。 ユーザーを指定しないと、現在のセキュリティ コンテキストが使用されます。 たとえば、次のコマンドは、RegisterRExt.exe をコマンド プロンプトを開いたユーザーの資格情報のパスでインスタンスにパッケージの管理を有効します。

    `REgisterRExt.exe /installpkgmgmt`

3. 特定のデータベースにパッケージの管理を追加するには、管理者特権でコマンド プロンプトから次のコマンドを実行します。

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    このコマンドは、ユーザーのアクセス許可を制御するために使用される次のデータベース ロールを含む一部のデータベース アイテムを作成します。 `rpkgs-users`、 `rpkgs-private`、および`rpkgs-shared`です。

    たとえば、次のコマンドは、RegisterRExt を実行しているインスタンス上のデータベース、パッケージの管理を使用できます。 ユーザーを指定しないと、現在のセキュリティ コンテキストが使用されます。

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

4. パッケージをインストールする必要がありますデータベースごとに、コマンドを繰り返します。

5. 新しいロールが正常に作成されたことを確認するには、SQL Server Management Studio でデータベースをクリックして、展開**セキュリティ**、展開と**データベース ロール**です。

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

この機能を有効にした後は、インストールまたはリモート R クライアントからのパッケージをアンインストールする RevoScaleR 関数を使用できます。

## <a name="bkmk_disable"></a> パッケージの管理を無効にします。

1. 管理者特権でコマンド プロンプトから RegisterRExt ユーティリティを再実行し、データベース レベルでのパッケージの管理を無効にします。

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、指定されたデータベースからパッケージの管理に関連するデータベース オブジェクトを削除します。 SQL Server コンピューターのセキュリティで保護されたファイル システムの場所からインストールされたすべてのパッケージも削除されます。

2. パッケージの管理が使用された各データベースでこのコマンドを繰り返します。

3.  (省略可能)前の手順を使用してパッケージのすべてのデータベースが消去された後は、管理者特権でコマンド プロンプトから次のコマンドを実行します。

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、インスタンスからパッケージの管理機能を削除します。 変更を確認するには、もう一度、スタート パッド サービスを手動で再起動する必要があります。

