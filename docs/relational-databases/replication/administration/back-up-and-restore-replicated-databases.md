---
title: "レプリケートされたデータベースのバックアップと復元 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バックアップ [SQL Server レプリケーション]"
  - "レプリケーションの管理, 復元"
  - "レプリケートされたデータベースのバックアップ"
  - "バックアップ [SQL Server レプリケーション], バックアップについて"
  - "レプリケートされたデータベースの復元 [SQL Server レプリケーション]"
  - "復旧 [SQL Server レプリケーション], 復旧について"
  - "データベースの復元 [SQL Server レプリケーション], レプリケートされたデータベース"
  - "データベースのバックアップ [SQL Server レプリケーション], レプリケートされたデータベース"
  - "復元 [SQL Server レプリケーション], 復元について"
  - "復旧 [SQL Server レプリケーション]"
  - "レプリケーション [SQL Server], 管理"
  - "分散データベース [SQL Server レプリケーション], バックアップ"
  - "復元 [SQL Server レプリケーション]"
  - "レプリケーションの管理, バックアップ"
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# レプリケートされたデータベースのバックアップと復元
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  レプリケートされたデータベースでは、データのバックアップと復元に対する特別な注意が必要です。 このトピックでは、それぞれの種類のレプリケーションのバックアップと復元の方法に関する概要、および詳細情報へのリンクを提供します。  
  
 レプリケーションでは、レプリケートされたデータベースをバックアップ作成元のサーバーおよびデータベースに復元する操作がサポートされます。 レプリケートされたデータベースのバックアップを別のサーバーまたはデータベースに復元する場合は、レプリケーションの設定は保存できません。 この場合、バックアップが復元された後で、すべてのパブリケーションとサブスクリプションを再作成する必要があります。  
  
> [!NOTE]  
>  ログ配布が使用されている場合は、レプリケートされたデータベースをスタンバイ サーバーに復元できます。 詳細については、次を参照してください。 [ログ配布とレプリケーション/#40 です。SQL Server と #41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)です。  
  
 レプリケートされたデータベースと関連付けられているシステム データベースは、定期的にバックアップする必要があります。 次のデータベースをバックアップします。  
  
-   パブリッシャーにあるパブリケーション データベース  
  
-   ディストリビューターにあるディストリビューション データベース  
  
-   各サブスクライバーにあるサブスクリプション データベース  
  
-   パブリッシャー、ディストリビューター、およびすべてのサブスクライバーにある **master** および **msdb** システム データベース。 これらのデータベースは、相互に関連するレプリケーション データベースとして、同時にバックアップする必要があります。 たとえば、バックアップ、 **マスター** と **msdb** 同時に、パブリッシャー データベースにパブリケーション データベースをバックアップします。 場合は、パブリケーション データベースで復元されていることを確認、 **マスター** と **msdb** データベースはレプリケーションの構成と設定の観点からのパブリケーション データベースと一致します。  
  
 定期的なログ バックアップを実行する場合は、レプリケーション関連の変更をログ バックアップでキャプチャする必要があります。 ログ バックアップを実行しない場合は、レプリケーションに関連する設定を変更するたびに、バックアップを実行する必要があります。 詳細については、「 [Common Actions Requiring an Updated Backup](../../../relational-databases/replication/administration/common-actions-requiring-an-updated-backup.md)」を参照してください。  
  
## バックアップと復元の方法  
 レプリケーション トポロジの各ノードのバックアップと復元の方法は、使用されるレプリケーションの種類によって異なります。 それぞれの種類のレプリケーションのバックアップと復元の方法の詳細については、以下のトピックを参照してください。  
  
-   [スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [マージ レプリケーションのバックアップと復元の方式](../../../relational-databases/replication/administration/strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 どの方法で復元を行う場合でも、必ずレプリケーションの設定の現在のスクリプトを安全な場所に保管しておいてください。 サーバーで障害が発生した場合やテスト環境をセットアップする必要がある場合は、サーバー名の参照を変更してスクリプトを修正し、そのスクリプトをレプリケーションの設定の再作成に利用することができます。 現在のレプリケーションの設定用のスクリプトの他に、レプリケーションを有効にするスクリプトと無効にするスクリプトを作成する必要があります。 レプリケーション オブジェクト スクリプト作成方法の詳細については、次を参照してください。 [Scripting レプリケーション](../../../relational-databases/replication/scripting-replication.md)します。  
  
## 参照  
 [SQL Server データベースのバックアップと復元](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [レプリケーション管理の推奨事項](../../../relational-databases/replication/administration/best-practices-for-replication-administration.md)  
  
  