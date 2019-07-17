---
title: 有効にするか、リモート R パッケージの管理 - SQL Server Machine Learning サービスを無効にします。
description: リモート SQL Server 2016 R Services または SQL Server 2017 の Machine Learning Services (In-database) での R パッケージの管理を有効にします。
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: ea567d8fbe3f6bbd9b51133ec015768cd4c6e893
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962527"
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>有効にするか、SQL Server のリモート パッケージの管理を無効にします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、クライアント ワークステーションまたは別の Machine Learning Server から R パッケージのリモート管理を有効にする方法について説明します。 SQL Server で、パッケージの管理機能を有効にすると、SQL Server にパッケージをインストールするのにクライアントで RevoScaleR コマンドを使用できます。

> [!NOTE]
> 現在の R ライブラリの管理がサポートされています。ロードマップが Python をサポートします。

既定では、SQL Server の外部のパッケージ管理機能は無効になります。 次のセクションで説明した機能を有効に個別のスクリプトを実行する必要があります。

## <a name="overview-of-process-and-tools"></a>プロセスとツールの概要

を有効にするまたは SQL Server 上のパッケージ管理を無効にするには、コマンド ライン ユーティリティを使用して**RegisterRExt.exe**、に含まれている、 **RevoScaleR**パッケージ。

[有効にする](#bkmk_enable)この機能は、データベース管理者が必要とする、2 段階のプロセス: (SQL Server インスタンスごと)、SQL Server インスタンス上のパッケージ管理を有効にし、パッケージ管理 (SQL Server ごとに SQL database を有効にします。データベースの場合)。

[無効にすると](#bkmk_disable)パッケージの管理機能では、multipel 手順も必要です。 データベース レベルのパッケージと (データベース) ごとのアクセス許可を削除し (1 回あたりのインスタンス) サーバーから役割を削除します。

## <a name="bkmk_enable"></a> パッケージの管理を有効にします。

1. SQL Server で、管理者特権のコマンド プロンプトを開くし、ユーティリティでは、RegisterRExt.exe を含むフォルダーに移動します。 既定の場所は`<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`します。

2. 環境内の適切な引数を指定して、次のコマンドを実行します。

    `RegisterRExt.exe /install pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、パッケージの管理に必要な SQL Server コンピューターのインスタンス レベルのオブジェクトを作成します。 また、インスタンスのスタート パッドを再起動します。

    インスタンスを指定しない場合は、既定のインスタンスが使用されます。 ユーザーを指定しない場合は、現在のセキュリティ コンテキストが使用されます。 たとえば、次のコマンドでは、RegisterRExt.exe、コマンド プロンプトを開いたユーザーの資格情報のパスのインスタンスでパッケージの管理が有効。 にします。

    `REgisterRExt.exe /install pkgmgmt`

3. 特定のデータベースにパッケージの管理を追加するには、管理者特権でコマンド プロンプトから次のコマンドを実行します。

    `RegisterRExt.exe /install pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    このコマンドは、ユーザーのアクセス許可を制御するために使用される次のデータベース ロールを含む、一部のデータベース アイテムを作成します: `rpkgs-users`、 `rpkgs-private`、および`rpkgs-shared`します。

    たとえば、次のコマンドは、RegisterRExt が実行されているインスタンス上のデータベース、パッケージの管理を使用できます。 ユーザーを指定しない場合は、現在のセキュリティ コンテキストが使用されます。

    `RegisterRExt.exe /install pkgmgmt /database:TestDB`

4. パッケージをインストールする必要がありますデータベースごとに、コマンドを繰り返します。

5. 新しいロールが正常に作成されたことを確認するには、SQL Server Management studio でデータベースをクリックします。 を展開**セキュリティ**、展開と**データベース ロール**します。

    Sys.database_principals、次のようにクエリを実行することもできます。

    ```sql
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

1. 管理者特権でコマンド プロンプトでは、もう一度、RegisterRExt ユーティリティを実行し、データベース レベルでのパッケージ管理を無効にします。

    `RegisterRExt.exe /uninstall pkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、指定されたデータベースからパッケージの管理に関連するデータベース オブジェクトを削除します。 SQL Server コンピューターのセキュリティで保護されたファイル システムの場所からインストールされたすべてのパッケージも削除されます。

2. パッケージの管理が使用された各データベースでは、このコマンドを繰り返します。

3.  (省略可能)前の手順を使用してパッケージのすべてのデータベースが消去された後、管理者特権でコマンド プロンプトから、次のコマンドを実行します。

    `RegisterRExt.exe /uninstall pkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、インスタンスからパッケージの管理機能を削除します。 手動で変更を表示するには、もう一度、スタート パッド サービスを再起動する必要があります。

## <a name="next-steps"></a>次の手順

+ [RevoScaleR を使用して、新しい R パッケージをインストールするには](use-revoscaler-to-manage-r-packages.md)
+ [R パッケージをインストールするためのヒント](packages-installed-in-user-libraries.md)
+ [既定のパッケージ](../package-management/default-packages.md)
