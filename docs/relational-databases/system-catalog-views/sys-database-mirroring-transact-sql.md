---
title: sys.database_mirroring (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring
- database_mirroring
- sys.database_mirroring_TSQL
- database_mirroring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_mirroring catalog view
ms.assetid: 480de2b0-2c16-497d-a6a3-bf7f52a7c9a0
caps.latest.revision: 53
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 50b7b4df6a6583831c81b021db98df2a42fc3620
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdatabasemirroring-transact-sql"></a>sys.database_mirroring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンス内の各データベースの 1 つの行を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 場合、データベースがオンラインでない場合、またはデータベース ミラーリングが有効でない場合 database_id を除くすべての列の値は NULL になります。  
  
 Master または tempdb 以外のデータベースの行を表示するには、する必要がありますかデータベースの所有者またはが少なくとも ALTER ANY DATABASE または VIEW ANY DATABASE のサーバー レベルの権限か、master データベースの CREATE DATABASE 権限。 ミラー データベースで NULL 以外の値を表示するには、メンバーである、 **sysadmin**固定サーバー ロール。  
  
> [!NOTE]  
>  データベースがミラーリングに参加していない場合、「mirroring _」の付いたすべての列は NULL を使用します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|データベースの ID です。 インスタンス内で一意では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**mirroring_guid**|**uniqueidentifier**|ミラー化のパートナーシップの ID。<br /><br /> NULL = データベースがアクセスできるか、ミラー化されていません。<br /><br /> メモ: 場合は、データベースがミラーリングに参加していない、「mirroring _」の付いたすべての列は NULL です。|  
|**mirroring_state**|**tinyint**|ミラー データベースとデータベース ミラーリング セッションの状態です。<br /><br /> 0 = 中断状態<br /><br /> 1 = 他のパートナーから切断<br /><br /> 2 = 同期中<br /><br /> 3 = フェールオーバーを保留しています<br /><br /> 4 = 同期済み<br /><br /> 5 = パートナーが同期されていません。 現在フェールオーバーはできません。<br /><br /> 6 = パートナーが同期されています。 フェールオーバーできる可能性があります。 フェールオーバーでは、「要件については[Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)です。<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_state_desc**|**nvarchar(60)**|ミラー データベースとデータベース ミラーリング セッションの状態の説明。次のいずれかになります。<br /><br /> DISCONNECTED<br /><br /> SYNCHRONIZED<br /><br /> SYNCHRONIZING<br /><br /> PENDING_FAILOVER<br /><br /> SUSPENDED<br /><br /> UNSYNCHRONIZED<br /><br /> SYNCHRONIZED<br /><br /> NULL<br /><br /> 詳細については、「[ミラーリング状態 &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)」を参照してください。|  
|**mirroring_role**|**tinyint**|データベース ミラーリング セッションにおけるローカル データベースの現在のロールです。<br /><br /> 1 = プリンシパル<br /><br /> 2 = ミラー<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_role_desc**|**nvarchar(60)**|ミラー化におけるローカル データベースのロールの説明。次のいずれかになります。<br /><br /> PRINCIPAL<br /><br /> MIRROR|  
|**mirroring_role_sequence**|**int**|フェールオーバーまたは強制されたサービスにより、ミラー化のパートナーがプリンシパル ロールとミラー ロールを切り替えた回数。<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_safety_level**|**tinyint**|ミラー データベースの更新に関する安全性の設定。<br /><br /> 0 = 状態不明<br /><br /> 1 = オフ [非同期]<br /><br /> 2 = 完全 (同期)<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_safety_level_desc**|**nvarchar(60)**|ミラー データベースの更新に関するトランザクションの安全性の設定。次のいずれかになります。<br /><br /> UNKNOWN<br /><br /> OFF<br /><br /> FULL<br /><br /> NULL|  
|**mirroring_safety_sequence**|**int**|トランザクションの安全性レベルに変更が行われた場合の更新シーケンス番号。<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_partner_name**|**nvarchar(128)**|データベース ミラーリング パートナーのサーバー名。<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_partner_instance**|**nvarchar(128)**|他のパートナーに対するインスタンス名とコンピューター名。 クライアントがプリンシパル サーバーとなる場合、クライアントからパートナーに接続するにはこの情報が必要です。<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_witness_name**|**nvarchar(128)**|データベース ミラーリング監視サーバーのサーバー名。<br /><br /> NULL = ミラーリング監視サーバーが存在しません。|  
|mirroring_witness_state|**tinyint**|データベースのデータベース ミラーリング セッションにおけるミラーリング監視サーバーの状態。次のいずれかになります。<br /><br /> 0 = 不明<br /><br /> 1 = 接続<br /><br /> 2 = 切断<br /><br /> NULL = ミラーリング監視サーバーが存在しないか、データベースがオンラインになっていない、またはデータベースがミラー化されていません。|  
|**mirroring_witness_state_desc**|**nvarchar(60)**|状態の説明。次のいずれかになります。<br /><br /> UNKNOWN<br /><br /> CONNECTED<br /><br /> DISCONNECTED<br /><br /> NULL|  
|**mirroring_failover_lsn**|**numeric(25,0)**|両方のパートナーのディスクに保存されることが保証されている最新のトランザクション ログ レコードのログ シーケンス番号 (LSN)。 フェールオーバー後、 **mirroring_failover_lsn**の調整が新しいミラー サーバーが、新しいプリンシパル データベースと、新しいミラー データベースを同期するために開始点として、パートナーによって使用されます。|  
|**mirroring_connection_timeout**|**int**|ミラー化接続のタイムアウト (秒単位)。 これは、パートナーまたはミラーリング監視サーバーからの返信を待機する秒数です。この時間を過ぎるとパートナーまたはミラーリング監視サーバーは使用できないものと見なされます。 タイムアウトの既定値は 10 秒です。<br /><br /> NULL= データベースにアクセスできないか、ミラー化されていません。|  
|**mirroring_redo_queue**|**int**|ミラー化で再実行されるログの最大サイズ。 Mirroring_redo_queue_type が既定の設定はの UNLIMITED に設定されている場合、この列は NULL を使用します。 データベースがオンラインでない場合も、この列は NULL になります。<br /><br /> 上記以外の場合、この列にはログの最大サイズ (MB 単位) が格納されます。 最大値に到達すると、ミラー サーバーが遅れを取り戻すまで、ログはプリンシパルで一時停止されます。 この機能によって、フェールオーバー時間が制限されます。<br /><br /> 詳細については、「[役割の交代中に発生するサービスの中断時間の算出 &#40;データベース ミラーリング&#41;](../../database-engine/database-mirroring/estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)」を参照してください。|  
|**mirroring_redo_queue_type**|**nvarchar(60)**|UNLIMITED の場合、ミラー化で再実行キューが制限されないことを示します。 これが既定の設定です。<br /><br /> MB の場合、再実行キューの最大サイズが MB 単位で制限されることを示します。 キュー サイズをキロバイト単位またはギガバイト、として指定された場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]値をメガバイト単位に変換します。<br /><br /> データベースがオンラインでない場合、この列は NULL になります。|  
|**mirroring_end_of_log_lsn**|**numeric(25,0)**|ディスクにフラッシュされたローカルの end-of-log。 これは、ミラー サーバーから書き込まれた LSN を比較 (を参照してください、 **mirroring_failover_lsn**列)。|  
|**mirroring_replication_lsn**|**numeric(25,0)**|レプリケーションが送信できる最大 LSN。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)   
 [データベースとファイルのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
