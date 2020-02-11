---
title: ミラー化されたデータベースのダウンタイムを最小限に抑えて、システムに Service Pack をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- hotfixes [SQL Server]
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
- service packs [SQL Server]
- upgrading mirrored database systems
- upgrading SQL Server, mirrored databases
ms.assetid: bdc63142-027d-4ead-9d3e-147331387ef5
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 821fd05e94ac820dff50bd08c70c75e7e9cc653d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62779596"
---
# <a name="install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases"></a>ミラー化されたデータベースのダウンタイムを最小限に抑えた Service Pack のシステムへのインストール
  このトピックでは、Service Pack および修正プログラムをインストールする際に、ミラー化されたデータベースのダウンタイムを最小限に抑える方法について説明します。 このプロセスには、データベース ミラーリングに参加している [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] のインスタンスを順次アップグレードする処理が伴います。 この形式の更新プログラム (*ローリングアップデート*と呼ばれます) によって、ダウンタイムが1つのフェールオーバーのみに短縮されます。 ただし、ミラー サーバーとプリンシパル サーバーが地理的に離れている高パフォーマンス モードのセッションでは、ローリング アップデートは適しません。  
  
 ローリング アップデートは、次の複数の段階から成るプロセスです。  
  
-   データを保護する。  
  
-   セッションにミラーリング監視サーバーが含まれる場合は、ミラーリング監視サーバーを削除しておくことをお勧めします。 そうしないと、ミラー サーバー インスタンスをアップデートする際のデータベースの可用性が、プリンシパル サーバー インスタンスに接続されたミラーリング監視サーバーに依存することになります。 削除したミラーリング監視サーバーは、ローリング アップデート プロセス中にいつでもアップデートでき、また、そうすることでデータベースのダウンタイムを最小限に抑えることができます。  
  
    > [!NOTE]  
    >  詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 &#40;データベース ミラーリング&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。  
  
-   セッションが高パフォーマンス モードで動作している場合は、動作モードを高い安全性モードに変更する。  
  
-   データベース ミラーリングに参加している各サーバー インスタンスをアップデートする。 ローリング アップデートでは、現在ミラー サーバーであるサーバー インスタンスをアップグレードし、ミラー化された各データベースを手動でフェールオーバーして、さらに、元はプリンシパル サーバーであった (新しいミラー サーバーになる) サーバー インスタンスをアップグレードする作業が伴います。 この時点で、ミラーリングを再開する必要があります。  
  
    > [!NOTE]  
    >  ローリング アップデートを開始する前に、少なくとも 1 つのミラーリング セッションで試験的に手動フェールオーバーを実行しておくことをお勧めします。  
  
-   必要に応じて、高パフォーマンス モードに戻す。  
  
-   必要に応じて、ミラーリング監視サーバーをミラーリング セッションに戻す。  
  
 ここでは、各段階の手順について説明します。  
  
> [!IMPORTANT]  
>  同時実行ミラーリング セッションでは、1 つのサーバー インスタンスが複数の異なるミラーリング ロール (プリンシパル サーバー、ミラー サーバー、またはミラーリング監視サーバー) を実行している場合があります。 この場合は、基本的なローリング アップデート プロセスを適宜調整する必要があります。  
  
### <a name="to-protect-your-data-before-an-update-a-best-practice"></a>アップデート前にデータを保護するには (ベスト プラクティス)  
  
1.  すべてのプリンシパルデータベースでデータベースの完全バックアップを実行します。  
  
     **データベースをバックアップするには**  
  
    -   [SQL Server&#41;&#40;データベースの完全バックアップを作成](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)します。  
  
2.  すべてのプリンシパル データベースで [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) コマンドを実行します。  
  
### <a name="to-remove-a-witness-from-a-session"></a>ミラーリング監視サーバーをセッションから削除するには  
  
1.  ミラーリング セッションにミラーリング監視サーバーが存在する場合は、ローリング アップデートの実行前にミラーリング監視サーバーを削除しておくことをお勧めします。  
  
     **ミラーリング監視サーバーを削除するには**  
  
    -   [データベースミラーリングセッションからミラーリング監視サーバーを削除 &#40;SQL Server&#41;](database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a>セッションを高パフォーマンス モードから高い安全性モードに変更するには  
  
1.  ミラーリング セッションを高パフォーマンス モードで実行している場合は、ローリング アップデートを実行する前に、動作モードを、自動フェールオーバーを伴わない高い安全性モードに変更します。 以下の方法のうちのいずれか 1 つを使用します。  
  
    -   
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページで、[[動作モード]](../relational-databases/databases/database-properties-mirroring-page.md) オプションを **[自動フェールオーバーを伴わない高い安全性 (同期)]** に変更します。 このページにアクセスする方法については、「[データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)」を参照してください。  
  
    -   
  [!INCLUDE[tsql](../includes/tsql-md.md)]: トランザクションの安全性を FULL に設定します。 詳細については、｢[データベース ミラーリング セッションでのトランザクションの安全性の変更 &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)」を参照してください。  
  
### <a name="to-perform-the-rolling-update"></a>ローリング アップデートを実行するには  
  
1.  ローリング アップデートを開始する際は、ダウンタイムを最小限に抑えるため、すべてのミラーリング セッションにおいてミラー サーバーとして機能しているミラーリング パートナーから先に更新することをお勧めします。 場合によっては、この時点で複数のサーバー インスタンスを更新する必要があります。  
  
    > [!NOTE]  
    >  ミラーリング監視サーバーは、ローリング アップデート プロセス中、いつでもアップデートできます。 たとえば、セッション 1 ではミラー サーバーとして、セッション 2 ではミラーリング監視サーバーとして機能しているサーバー インスタンスであれば、今すぐにアップデートすることもできます。  
  
     最初にアップデートするサーバー インスタンスは、ミラーリング セッションが現在どのように構成されているかによって異なります。その指針を次に示します。  
  
    -   サーバー インスタンスがそのすべてのミラーリング セッションにおいて既にミラー サーバーとして機能している場合、そのサーバー インスタンスに Service Pack または修正プログラムをインストールします。  
  
    -   どのサーバー インスタンスもいずれかのミラーリング セッションのプリンシパル サーバーとして機能している場合は、最初にアップデートするサーバー インスタンスを 1 つ選択します。 次に、選択したサーバー インスタンスの各プリンシパル データベースを手動でフェールオーバーし、Service Pack または修正プログラムをインストールしてそのサーバー インスタンスをアップデートします。  
  
     アップデート後のサーバー インスタンスは、自動的にそれぞれのミラーリング セッションに再度参加します。  
  
     **手動フェールオーバーを実行するには**  
  
    -   [データベースミラーリングセッションを手動でフェールオーバーする &#40;SQL Server Management Studio&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Transact-sql&#41;&#40;データベースミラーリングセッションを手動でフェール](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)オーバーします。  
  
     手動フェールオーバーのしくみについては、「[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)」を参照してください。  
  
2.  前の手順でアップデートしたミラー サーバー インスタンスのすべてのミラーリング セッションの同期が完了するまで待ちます。 次に、プリンシパル サーバー インスタンスに接続し、セッションを手動でフェールオーバーします。 フェールオーバー時は、アップデートされたサーバー インスタンスがそのセッションのプリンシパル サーバーになり、以前のプリンシパル サーバーがミラー サーバーになります。  
  
     この手順の目的は、すべてのミラーリング セッションで、パートナー関係にある他方のサーバー インスタンスがミラー サーバーとなるようにすることです。  
  
3.  フェールオーバー後は、プリンシパル データベースに対して [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) コマンドを実行することをお勧めします。  
  
4.  すべてのミラーリング セッションで、ミラー サーバー (パートナー) になった各サーバー インスタンスに Service Pack または修正プログラムをインストールします。 場合によっては、この時点で複数のサーバーを更新する必要があります。  
  
    > [!IMPORTANT]  
    >  複雑なミラーリング構成の場合、一部のサーバー インスタンスが、1 つまたは複数のミラーリング セッションで元のプリンシパル サーバーとして機能している場合があります。 関連するすべてのインスタンスが更新されるまで、これらのサーバーインスタンスに対して手順2-4 を繰り返します。  
  
5.  ミラーリング セッションを再開します。  
  
    > [!NOTE]  
    >  自動フェールオーバーは、ミラーリング監視サーバーがアップデートされるまで機能しません。  
  
6.  すべてのミラーリング セッションの残りのサーバー インスタンス (ミラーリング監視サーバー) に Service Pack または修正プログラムをインストールします。 アップデートしたミラーリング監視サーバーをミラーリング セッションに再度参加させると、自動フェールオーバーが有効になります。 場合によっては、この時点で複数のサーバーを更新する必要があります。  
  
### <a name="to-return-a-session-to-high-performance-mode"></a>セッションを高パフォーマンス モードに戻すには  
  
1.  必要に応じて、高パフォーマンス モードに戻す場合は、次のいずれかの方法を使用します。  
  
    -   
  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページで、 [[動作モード]](../relational-databases/databases/database-properties-mirroring-page.md) オプションを **[高パフォーマンス (非同期)]** に変更します。  
  
    -   : [!INCLUDE[tsql](../includes/tsql-md.md)] [ALTER database](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)を使用して、トランザクションの安全性を OFF に設定します。  
  
### <a name="to-return-a-witness-to-a-mirroring-session"></a>ミラーリング監視サーバーをミラーリングセッションに戻すには  
  
1.  必要に応じて、高い安全性モードで、各ミラーリング セッションのミラーリング監視サーバーを再度確立します。  
  
     **ミラーリング監視サーバーを削除するには**  
  
    -   [データベースミラーリング監視サーバーを追加または置き換える &#40;SQL Server Management Studio&#41;](database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [Windows 認証 &#40;使用してデータベースミラーリング監視サーバーを追加する Transact-sql&#41;](database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE データベースミラーリング &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Transact-sql&#41;のバックアップ &#40;](/sql/t-sql/statements/backup-transact-sql)   
 [データベースミラーリング &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md)   
 [データベースミラーリングの動作モード](database-mirroring/database-mirroring-operating-modes.md)   
 [データベースミラーリングセッション中の役割の交代 &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)   
 [&#40;SQL Server Management Studio を開始データベースミラーリングモニター&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [ミラー化されたデータベース &#40;SQL Server Management Studio の状態を表示&#41;](database-mirroring/view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
  
