---
title: 'アクティブなセカンダリ: セカンダリレプリカでのバックアップ (Always On 可用性グループ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0cf899cdbeb1ae4ede6c9196b8eb93a9d9e54f05
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937243"
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a>アクティブなセカンダリ: セカンダリ レプリカでのバックアップ (AlwaysOn 可用性グループ)
  [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のアクティブなセカンダリ機能では、セカンダリ レプリカでのバックアップ操作の実行をサポートしています。 バックアップ操作では、(バックアップ圧縮により) I/O と CPU に大きな負荷がかかる場合があります。 同期済みまたは同期中のセカンダリ レプリカへバックアップをオフロードすることで、ワークロードが最も多いプライマリ レプリカをホストするサーバー インスタンスでリソースを使用できるようにします。  
  
> [!NOTE]  
>  可用性グループのプライマリ データベースとセカンダリ データベースでは、RESTORE ステートメントを使用できません。  
  
  
  
##  <a name="backup-types-supported-on-secondary-replicas"></a><a name="SupportedBuTypes"></a> セカンダリ レプリカでサポートされるバックアップの種類  
  
-   セカンダリ レプリカで実行されたときに `BACKUP DATABASE` でサポートされるのは、データベース、ファイル、またはファイル グループのコピーのみの完全バックアップだけです。 コピーのみのバックアップはログ チェーンには影響しません。また、コピーのみのバックアップを実行しても、差分ビットマップは消去されません。  
  
-   差分バックアップは、セカンダリ レプリカではサポートされていません。  
  
-   **BACKUP LOG** でサポートされるのは通常のログ バックアップだけです (セカンダリ レプリカでのログ バックアップでは、COPY_ONLY オプションはサポートされていません)。  
  
     可用性モード (同期コミットまたは非同期コミット) に関係なく、任意のレプリカ (プライマリまたはセカンダリ) で取得されたログ バックアップ全体にわたって一貫性のあるログ チェーンが保証されます。  
  
-   セカンダリ データベースをバックアップするには、セカンダリ レプリカがプライマリ レプリカと通信可能で、`SYNCHRONIZED` または `SYNCHRONIZING` であることが必要です。  
  
##  <a name="configuring-where-backup-jobs-run"></a><a name="WhereBuJobsRun"></a> バックアップ ジョブを実行する場所の構成  
 セカンダリ レプリカでバックアップを実行してプライマリ運用サーバーからバックアップ ワークロードをオフロードすると、非常に大きな利点があります。 ただし、セカンダリ レプリカでバックアップを実行する場合は、バックアップ ジョブを実行する場所を決定するプロセスは非常に複雑です。 これに対処するには、バックアップ ジョブを実行する場所を次のように構成します。  
  
1.  可用性グループを構成して、バックアップを優先的に実行する可用性レプリカを指定します。 詳細については、「 *CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;* 」または「 *ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;* 」の [CREATE AVAILABILITY GROUP &amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/create-availability-group-transact-sql) または [ALTER AVAILABILITY GROUP &amp;#40;Transact-SQL&amp;#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)であることが必要です。  
  
2.  バックアップの実行の候補である可用性レプリカをホストするすべてのサーバー インスタンス上のすべての可用性データベースに対して、スクリプト化されたバックアップ ジョブを作成します。 詳細については、「 [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md) を参照してください。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
 **セカンダリ レプリカでバックアップを構成するには**  
  
-   [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
 **現在のレプリカが推奨されるバックアップ レプリカであるかどうかを判別するには**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 **バックアップ ジョブを作成するには**  
  
-   [メンテナンス プラン ウィザードの使用](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [ジョブの実装](../../../ssms/agent/implement-jobs.md)  
  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [コピーのみのバックアップ &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
