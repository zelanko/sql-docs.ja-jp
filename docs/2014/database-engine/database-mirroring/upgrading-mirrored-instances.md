---
title: サーバーインスタンスをアップグレードするときに、ミラー化されたデータベースのダウンタイムを最小限に抑える |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- upgrading SQL Server, rolling upgrade of mirrored databases
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
ms.assetid: 0e73bd23-497d-42f1-9e81-8d5314bcd597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 857e18b1b956d3d8c9d2fc4c5692dbf022bf85fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62754282"
---
# <a name="minimize-downtime-for-mirrored-databases-when-upgrading-server-instances"></a>サーバー インスタンスのアップグレード時に、ミラー化されたデータベースのダウンタイムを最小化する方法
  サーバーインスタンスをに[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]アップグレードする場合は、*ローリングアップグレード*と呼ばれる順次アップグレードを実行することで、ミラー化された各データベースのダウンタイムを1回の手動フェールオーバーのみに減らすことができます。 ローリング アップグレードは複数の段階から成るプロセスです。最も単純な形式では、ミラーリング セッションで現在ミラー サーバーとして機能しているサーバー インスタンスをアップグレードした後、ミラー化されたデータベースを手動でフェールオーバーし、以前のプリンシパル サーバーをアップグレードして、ミラーリングを再開します。 実際に実行するプロセスは、動作モードと、アップグレードするサーバー インスタンスで実行しているミラーリング セッションの数やレイアウトによって異なります。  
  
> [!NOTE]  
>  ローリングアップグレードを実行して Service Pack または修正プログラムをインストールする方法については、「[ミラー化されたデータベースのダウンタイムを最小限に抑えてシステムに Service pack をインストール](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md)する」を参照してください。  
  
 **推奨される準備 (ベスト プラクティス)**  
  
 ローリング アップグレードを開始する前に以下を実行することをお勧めします。  
  
1.  少なくとも 1 つのミラーリング セッションで試験的に手動フェールオーバーを実行します。  
  
    -   [データベースミラーリングセッションを手動でフェールオーバーする &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Transact-sql&#41;&#40;データベースミラーリングセッションを手動でフェール](manually-fail-over-a-database-mirroring-session-transact-sql.md)オーバーします。  
  
    > [!NOTE]  
    >  手動フェールオーバーのしくみについては、「[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)」を参照してください。  
  
2.  データを保護します。  
  
    1.  すべてのプリンシパル データベースを対象にデータベースの完全バックアップを実行します。  
  
         [SQL Server&#41;&#40;データベースの完全バックアップを作成](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)します。  
  
    2.  すべてのプリンシパル データベースで [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) コマンドを実行します。  
  
 **ローリング アップグレードの段階**  
  
 ローリング アップグレードの個々の段階は、ミラーリング構成の動作モードによって異なります。 ただし、基本的な段階は同じです。  
  
> [!NOTE]  
>  動作モードの詳細については、「 [データベース ミラーリングの動作モード](database-mirroring-operating-modes.md)」を参照してください。  
  
 次の図は、動作モードごとにローリング アップグレードの基本的な段階をフローチャートで示したものです。 図の後で、対応する各手順について説明します。  
  
 ![ローリング アップグレードの手順のフローチャート](../media/dbm-rolling-upgrade.gif "ローリング アップグレードの手順のフローチャート")  
  
> [!IMPORTANT]  
>  同時実行ミラーリング セッションでは、1 つのサーバー インスタンスが複数の異なるミラーリング ロール (プリンシパル サーバー、ミラー サーバー、またはミラーリング監視サーバー) を実行している場合があります。 この場合は、基本的なローリング アップグレード プロセスを適宜調整する必要があります。 詳細については、「[データベース ミラーリング セッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)」を参照してください。  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a>セッションを高パフォーマンス モードから高い安全性モードに変更するには  
  
1.  ミラーリング セッションを高パフォーマンス モードで実行している場合は、ローリング アップグレードを実行する前に、動作モードを、自動フェールオーバーを伴わない高い安全性モードに変更します。  
  
    > [!IMPORTANT]  
    >  ミラー サーバーとプリンシパル サーバーが地理的に離れている場合は、ローリング アップグレードは適しません。  
  
    -   
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページで、[[動作モード]](../../relational-databases/databases/database-properties-mirroring-page.md) オプションを **[自動フェールオーバーを伴わない高い安全性 (同期)]** に変更します。 このページにアクセスする方法については、「[データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)」を参照してください。  
  
    -   
  [!INCLUDE[tsql](../../includes/tsql-md.md)]: トランザクションの安全性を FULL に設定します。 詳細については、「[データベースミラーリングセッションでのトランザクションの安全性の変更 &#40;transact-sql&#41;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md) 」を参照してください。  
  
### <a name="to-remove-a-witness-from-a-session"></a>ミラーリング監視サーバーをセッションから削除するには  
  
1.  ミラーリング セッションにミラーリング監視サーバーが存在する場合は、ローリング アップグレードの実行前にミラーリング監視サーバーを削除しておくことをお勧めします。 そうしないと、ミラー サーバー インスタンスをアップグレードする際のデータベースの可用性が、プリンシパル サーバー インスタンスに接続されたミラーリング監視サーバーに依存することになります。 削除したミラーリング監視サーバーは、ローリング アップグレード プロセス中にいつでもアップグレードでき、また、そうすることでデータベースのダウンタイムを最小限に抑えることができます。  
  
    > [!NOTE]  
    >  詳細については、「[クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 &#40;データベース ミラーリング&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)」を参照してください。  
  
    -   [データベースミラーリングセッションからミラーリング監視サーバーを削除 &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-perform-the-rolling-upgrade"></a>ローリング アップグレードを実行するには  
  
1.  ローリング アップグレードを開始する際は、ダウンタイムを最小限に抑えるため、すべてのミラーリング セッションにおいてミラー サーバーとして機能しているミラーリング パートナーから先に更新することをお勧めします。 場合によっては、この時点で複数のサーバー インスタンスを更新する必要があります。  
  
    > [!NOTE]  
    >  ミラーリング監視サーバーは、ローリング アップグレード プロセス中、いつでもアップグレードできます。 たとえば、セッション 1 ではミラー サーバーとして、セッション 2 ではミラーリング監視サーバーとして機能しているサーバー インスタンスであれば、今すぐにアップグレードすることもできます。  
  
     最初にアップグレードするサーバー インスタンスは、ミラーリング セッションが現在どのように構成されているかによって異なります。その指針を次に示します。  
  
    -   サーバー インスタンスがそのすべてのミラーリング セッションにおいて既にミラー サーバーとして機能している場合、そのサーバー インスタンスを新しいバージョンにアップグレードします。  
  
    -   どのサーバー インスタンスもいずれかのミラーリング セッションのプリンシパル サーバーとして機能している場合は、最初にアップグレードするサーバー インスタンスを 1 つ選択します。 次に、選択したサーバー インスタンスの各プリンシパル データベースを手動でフェールオーバーし、そのサーバー インスタンスをアップグレードします。  
  
     アップグレード後のサーバー インスタンスは、自動的にそれぞれのミラーリング セッションに再度参加します。  
  
2.  前の手順でアップグレードしたミラー サーバー インスタンスのすべてのミラーリング セッションの同期が完了するまで待ちます。 次に、プリンシパル サーバー インスタンスに接続し、セッションを手動でフェールオーバーします。 フェールオーバー時は、アップグレードされたサーバー インスタンスがそのセッションのプリンシパル サーバーになり、以前のプリンシパル サーバーがミラー サーバーになります。  
  
     この手順の目的は、すべてのミラーリング セッションで、パートナー関係にある他方のサーバー インスタンスがミラー サーバーとなるようにすることです。  
  
     **アップグレード後のサーバーインスタンスにフェールオーバーした後の制限。**  
  
     以前のサーバー インスタンスから [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のサーバー インスタンスにフェールオーバーした後は、データベース セッションが中断されます。 もう一方のパートナーがアップグレードされるまで再開できません。 ただし、プリンシパル サーバーは引き続き接続を受け入れ、プリンシパル データベースに対するデータのアクセスや変更は許可されます。  
  
    > [!NOTE]  
    >  新しいミラーリング セッションを確立するには、すべてのサーバー インスタンスが同じバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行している必要があります。  
  
3.  フェールオーバー後は、プリンシパルデータベースで[DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)コマンドを実行することをお勧めします。  
  
4.  すべてのミラーリング セッションにおいて、現在ミラー サーバー (パートナー) となっている各サーバー インスタンスをアップグレードします。 場合によっては、この時点で複数のサーバーを更新する必要があります。  
  
    > [!IMPORTANT]  
    >  複雑なミラーリング構成の場合、一部のサーバー インスタンスが、1 つまたは複数のミラーリング セッションで元のプリンシパル サーバーとして機能している場合があります。 これらのサーバー インスタンスについては、関係するすべてのインスタンスがアップグレードされるまで、手順 2 から手順 4 までを繰り返してください。  
  
5.  ミラーリング セッションを再開します。  
  
    > [!NOTE]  
    >  自動フェールオーバーは、ミラーリング監視サーバーがアップグレードされてミラーリング セッションに戻されるまで機能しません。  
  
6.  すべてのミラーリング セッションの残りのサーバー インスタンス (ミラーリング監視サーバー) をアップグレードします。 アップグレードしたミラーリング監視サーバーをミラーリング セッションに再度参加させると、自動フェールオーバーが有効になります。 場合によっては、この時点で複数のサーバーを更新する必要があります。  
  
### <a name="to-return-a-session-to-high-performance-mode"></a>セッションを高パフォーマンス モードに戻すには  
  
1.  必要に応じて、高パフォーマンス モードに戻す場合は、次のいずれかの方法を使用します。  
  
    -   
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページで、 [[動作モード]](../../relational-databases/databases/database-properties-mirroring-page.md) オプションを **[高パフォーマンス (非同期)]** に変更します。  
  
    -   
  [!INCLUDE[tsql](../../includes/tsql-md.md)]: [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)を使用してトランザクションの安全性を OFF に設定します。  
  
### <a name="to-add-a-witness-back-into-a-mirroring-session"></a>ミラーリング監視サーバーをミラーリング セッションに戻すには  
  
1.  必要に応じて、高い安全性モードで、各ミラーリング セッションのミラーリング監視サーバーを再度確立します。  
  
     **ミラーリング監視サーバーを取得するには**  
  
    -   [データベースミラーリング監視サーバーを追加または置き換える &#40;SQL Server Management Studio&#41;](add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [Windows 認証 &#40;使用してデータベースミラーリング監視サーバーを追加する Transact-sql&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE データベースミラーリング &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Transact-sql&#41;のバックアップ &#40;](/sql/t-sql/statements/backup-transact-sql)   
 [ミラー化されたデータベース &#40;SQL Server Management Studio の状態を表示&#41;](view-the-state-of-a-mirrored-database-sql-server-management-studio.md)   
 [データベースミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [ミラー化されたデータベースのダウンタイムを最小限に抑えて、システムに Service Pack をインストールする](../install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases.md)   
 [データベースミラーリングセッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)   
 [データベースミラーリングセッションでのサービスの強制 Transact-sql&#41;の &#40;](force-service-in-a-database-mirroring-session-transact-sql.md)   
 [&#40;SQL Server Management Studio を開始データベースミラーリングモニター&#41;](start-database-mirroring-monitor-sql-server-management-studio.md)   
 [データベース ミラーリングの動作モード](database-mirroring-operating-modes.md)  
  
  
