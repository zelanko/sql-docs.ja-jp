---
title: Linux 上の SQL Server レプリケーションの構成 |Microsoft Docs
description: この記事では、Linux での SQL Server レプリケーションを構成する方法について説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 29c8dd4ef4898796722e1c54eeaff94afef1c0c6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66705339"
---
# <a name="configure-sql-server-replication-on-linux"></a>Linux 上の SQL Server レプリケーションを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] 紹介用の SQL Server レプリケーション Linux 上の SQL Server のインスタンス。

レプリケーションの詳細については、次を参照してください。 [SQL Server レプリケーションのドキュメント](../relational-databases/replication/sql-server-replication.md)します。

SQL Server Management Studio (SSMS) または Transact SQL ストアド プロシージャのいずれかを使った Linux 上のレプリケーションを構成します。

* SSMS を使用して、この記事の手順に従います。

  Windows オペレーティング システム上の SSMS を使用して、SQL Server のインスタンスに接続します。 背景と手順については、次を参照してください。 [SSMS を使用した Linux 上の SQL Server の管理に](./sql-server-linux-manage-ssms.md)します。
  
* 次のストアド プロシージャなど、 [Linux 上の SQL Server の構成のレプリケーション](sql-server-linux-replication-tutorial-tsql.md)チュートリアル。

## <a name="prerequisites"></a>前提条件

パブリッシャー、ディストリビューターおよびサブスクライバーを構成する前に、SQL Server インスタンスのいくつかの構成手順を完了する必要があります。

1. レプリケーション エージェントを使用する SQL Server エージェントを有効にします。 すべての Linux サーバーで、ターミナルで次のコマンドを実行します。

  ```bash
  sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
  sudo systemctl restart mssql-server
  ```

1. レプリケーション用の SQL Server インスタンスを構成します。 レプリケーション用の SQL Server インスタンスを構成するには、実行`sys.sp_MSrepl_createdatatypemappings`レプリケーションに参加しているすべてのインスタンス。

  ```sql
  USE msdb
  GO
  exec sys.sp_MSrepl_createdatatypemappings;
  GO
  ```

1. スナップショット フォルダーを作成します。 SQL Server エージェントでは、スナップショット フォルダーに対する読み取り/書き込みが必要です。 ディストリビューターでスナップショット フォルダーを作成します。

  スナップショット フォルダーを作成し、へのアクセスを付与する`mssql`ユーザーは、次のコマンドを実行します。

  ```bash
  sudo mkdir /var/opt/mssql/data/ReplData/
  sudo chown mssql /var/opt/mssql/data/ReplData/
  sudo chgrp mssql /var/opt/mssql/data/ReplData/
  ```

## <a name="configure-and-monitor-replication-with-sql-server-management-studio-ssms"></a>構成し、SQL Server Management Studio (SSMS) でのレプリケーションの監視

### <a name="configure-the-distributor"></a>ディストリビューターの構成
  
ディストリビューターを構成します。 

1. SSMS オブジェクト エクスプ ローラーで SQL Server のインスタンスに接続します。

1. 右クリックして**レプリケーション**、 をクリック**ディストリビューションの構成.** .

1. 指示に従って、**ディストリビューションの構成ウィザード**します。

### <a name="create-publication-and-articles"></a>パブリケーションとアーティクルを作成します。

パブリケーションとアーティクルを作成します。

1. オブジェクト エクスプ ローラーで次のようにクリックします**レプリケーション** > **ローカル パブリケーション**> **新しい公開しています。** .

1. 手順に従い、**パブリケーションの新規作成ウィザード**レプリケーション、およびパブリケーションに属するアーティクルの種類を構成します。

### <a name="configure-the-subscription"></a>サブスクリプションを構成します。

オブジェクト エクスプ ローラーで、サブスクリプションを構成する をクリックして**レプリケーション** > **ローカル サブスクリプション**> **新規サブスクリプション.** .

### <a name="monitor-replication-jobs"></a>レプリケーション ジョブの監視

レプリケーション ジョブを監視するのにには、レプリケーション モニターを使用します。

オブジェクト エクスプ ローラーで右クリックして**レプリケーション**、 をクリック**レプリケーション モニターの起動**します。

## <a name="next-steps"></a>次の手順

[概念:Linux 上の SQL Server レプリケーション](sql-server-linux-replication.md)

[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)します。
