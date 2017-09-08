---
title: "R パッケージの管理を有効または無効にする方法 | Microsoft Docs"
ms.custom: 
ms.date: 12/21/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: 7
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aac055d9a2337f1278d648fbcd17435afe1bd3b3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="r-package---how-to-enable-or-disable"></a>R パッケージ - 有効と無効の切り替え方法

既定では、R Services サービスがインストールされている場合でも、SQL Server インスタンスでのパッケージ管理は無効になります。 この機能を有効にする場合は、2 段階の処理で行います。この処理はデータベース管理者が行う必要があります。 

1. SQL Server インスタンス (SQL Server インスタンスごと) のパッケージ管理を有効にする 
2. SQL Database (SQL Server データベースごと) のパッケージ管理を有効にする 


パッケージの管理機能を無効にする場合、データベース レベルのパッケージとアクセス許可を削除し、サーバーからロールを削除するプロセスを逆行します。
 
1. 各データベース (データベースごと) のパッケージ管理を無効にする 
2. SQL Server インスタンス (インスタンスごと) のパッケージ管理を無効にする 

> [!IMPORTANT]
> この機能は開発中です。 構文や機能が今後のリリースで変更される可能性があることに注意してください。 

### <a name="to-enable-package-management"></a>パッケージ管理を有効にするには

パッケージ管理を有効または無効にするには、コマンド ライン ユーティリティ **RegisterRExt.exe**が必要です。これは、SQL Server R Services と共にインストールされる **RevoScaleR** パッケージに含まれています。 既定の場所は次のとおりです。

`<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe` 
    
1. 管理者特権のコマンド プロンプトを開き、次のコマンドを使用します。

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、パッケージ管理に必要なインスタンス レベルの成果物を SQL Server コンピューターに作成します。 

2. データベース レベルでパッケージ管理を追加する場合は、パッケージをインストールする必要があるデータベースごとに、管理者特権のコマンド プロンプトから次のコマンドを実行します。 

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]` 

    このコマンドは、ユーザーのアクセス許可を制御するために必要な **rpkgs-users**, **rpkgs-private**、および **rpkgs-shared**というデータベース ロールを含む、いくつかのデータベース成果物を作成します。 

### <a name="to-disable-package-management"></a>パッケージ管理を無効にするには 

1. 管理者特権のコマンド プロンプトから、次のコマンドを実行し、データベース レベルでパッケージ管理を無効にします。

   `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]` 

    このコマンドは、指定されたデータベースからパッケージ管理に関連するデータベース成果物を削除します。  また、このコマンドは、SQL Server コンピューター上の保護ファイル システムの場所からデータベースごとにインストールされたすべてのパッケージも削除します。
    
    コマンドは、パッケージ管理が使用されたデータベースごとに 1 回実行する必要があります。
 
2. (省略可能) インスタンスからパッケージ管理機能を完全に削除するには、前の手順ですべてのデータベースのパッケージを削除した後で、管理者特権のコマンド プロンプトから以下のコマンドを実行します。

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    このコマンドは、SQL Server インスタンスからパッケージ管理で使用されたインスタンス レベルの成果物を削除します。 


## <a name="see-also"></a>参照
[SQL Server R Services の R パッケージ管理](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)

