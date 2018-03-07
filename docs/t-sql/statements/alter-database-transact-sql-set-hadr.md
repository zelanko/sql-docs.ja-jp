---
title: ALTER DATABASE SET HADR (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET HADR
- SET_HADR_TSQL
- HADR_TSQL
- HADR
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER DATABASE statement, AlwaysOn Availability Group
- ALTER DATABASE statement, SET HADR options
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], Transact-SQL statements
- Availability Groups [SQL Server], databases
ms.assetid: 20e6e803-d6d5-48d5-b626-d1e0a73d174c
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a601a5f93f7a922228232c8ef4a91b5775eded91
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="alter-database-transact-sql-set-hadr"></a>ALTER DATABASE (Transact-SQL) SET HADR 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックには、設定の ALTER DATABASE の構文が含まれています。[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]セカンダリ データベースでのオプションです。 1 つだけの SET HADR オプションは ALTER DATABASE ステートメントごとに許可します。 これらのオプションは、セカンダリ レプリカ上でのみサポートされます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER DATABASE database_name  
   SET HADR   
   {  
        { AVAILABILITY GROUP = group_name | OFF }  
   | { SUSPEND | RESUME }  
   }  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 変更するセカンダリ データベースの名前を指定します。  
  
 SET HADR  
 指定された実行[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]コマンドを指定されたデータベースでします。  
  
 { AVAILABILITY GROUP **=***group_name* | OFF }  
 次のように、指定した可用性グループから可用性データベースを削除するか、指定した可用性グループに参加させます。  
  
 *group_name*  
 指定したデータベースをセカンダリ レプリカ上で参加させます。このレプリカは、group_name で指定された可用性グループにコマンドを実行するサーバー インスタンスによってホストされています。  
  
 この操作の前提条件は以下のとおりです。  
  
-   データベースは既にプライマリ レプリカ上の可用性グループに追加されている必要があります。  
  
-   プライマリ レプリカがアクティブになっている必要があります。 非アクティブなプライマリ レプリカをトラブルシューティングする方法の詳細についてを参照してください。[トラブルシューティング常に 可用性グループの構成 (SQL Server)](http://go.microsoft.com/fwlink/?LinkId=225834)です。  
  
-   プライマリ レプリカがオンラインになっており、セカンダリ レプリカがプライマリ レプリカに接続されている必要があります。  
  
-   セカンダリ データベースは、プライマリ データベースの最新のデータベースとログ バックアップから WITH NORECOVERY を使用して復元されている必要があります。これは、セカンダリ データベースがプライマリ データベースからの遅れを取り戻せるように最新のログ バックアップで終わっている必要があります。  
  
    > [!NOTE]  
    >  データベースを可用性グループを追加する、プライマリ レプリカをホストするサーバー インスタンスに接続し、使用して、、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md)*group_name*のデータベース追加*database_name*ステートメントです。  
  
 詳細については、「 [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。  
  
 OFF  
 指定したセカンダリ データベースを可用性グループから削除します。  
  
 セカンダリ データベースがプライマリ データベースから大幅に遅れており、セカンダリ データベースが遅れを取り戻すまで待てない場合は、セカンダリ データベースを削除することをお勧めします。 セカンダリ データベースを削除した後には、更新する一連のバックアップの (復元を使用しています...、最近使用したログ バックアップを復元することで WITH NORECOVERY)。  
  
> [!IMPORTANT]  
>  可用性グループから可用性データベースを完全に削除するには、プライマリ レプリカをホストするサーバー インスタンスに接続し、使用して、、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md)*group_name*削除データベース*availability_database_name*ステートメントです。 詳細については、次を参照してください[プライマリ データベースの可用性グループ &#40; から削除。SQL Server &#41;](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
 SUSPEND  
 セカンダリ データベースでデータ移動を中断します。 SUSPEND コマンドは、対象のデータベースをホストするレプリカによって受け付けられるとすぐに戻りますが、実際にはデータベースの中断が非同期に行われます。  
  
 その影響の範囲は、ALTER DATABASE ステートメントを実行する場所によって異なります。  
  
-   セカンダリ レプリカ上のセカンダリ データベースを中断した場合、ローカルのセカンダリ データベースのみが中断されます。 読み取り可能なセカンダリ上の既存の接続は、引き続き使用できます。 読み取り可能なセカンダリ上で中断されたデータベースに対する新しい接続は、データ移動が再開されるまでは許可されません。  
  
-   プライマリ レプリカ上のデータベースを中断した場合、すべてのセカンダリ レプリカ上の対応するセカンダリ データベースへのデータ移動が中断されます。 読み取り可能セカンダリ上の既存の接続は引き続き使用可能なおよび新しい読み取りを目的とした接続は読み取り可能なセカンダリ レプリカに接続できません。  
  
-   データ移動が強制的な手動フェールオーバーによって中断された場合、新しいセカンダリ レプリカへの接続は、データ移動が中断している間は許可されません。  
  
 セカンダリ レプリカ上のデータベースを中断した場合、データベースとレプリカは同期されなくなり、NOT SYNCHRONIZED とマークされます。  
  
> [!IMPORTANT]  
>  セカンダリ データベースが中断されている間、対応するプライマリ データベースの送信キューが未送信トランザクション ログ レコードに蓄積されます。 セカンダリ レプリカへの接続では、データ移動が中断されたときに使用可能であったデータが返されます。  
  
> [!NOTE]  
>  Always On セカンダリ データベースの再開の中断とは直接影響しません、プライマリ データベースの可用性セカンダリ データベースの中断に影響する場合、プライマリ データベースの冗長性とフェールオーバー機能まで、中断された場合セカンダリ データベースが再開されます。 ミラーリングの場合はこれと異なり、ミラーリングが再開されるまで、ミラーリングの状態はミラー データベースでもプリンシパル データベースでも中断になります。 Always On プライマリ データベースを中断すると、対応するすべてのセカンダリ データベースでデータ移動が中断され、そのデータベースの冗長性とフェールオーバー機能はプライマリ データベースが再開されるまで停止されます。  
  
 詳細については、次を参照してください[可用性データベース &#40; を一時停止。SQL Server &#41;](../../database-engine/availability-groups/windows/suspend-an-availability-database-sql-server.md).  
  
 RESUME  
 指定したセカンダリ データベース上で中断されたデータ移動を再開します。 RESUME コマンドは、対象のデータベースをホストするレプリカによって受け付けられるとすぐに戻りますが、実際にはデータベースの再開が非同期に行われます。  
  
 その影響の範囲は、ALTER DATABASE ステートメントを実行する場所によって異なります。  
  
-   セカンダリ レプリカ上のセカンダリ データベースを再開した場合、ローカルのセカンダリ データベースのみが再開されます。 データ移動は、データベースがプライマリ レプリカでも中断されている場合を除き、再開されます。  
  
-   プライマリ レプリカ上のデータベースを再開した場合、対応するセカンダリ データベースがローカルに中断されていないすべてのセカンダリ レプリカへのデータ移動が再開されます。 セカンダリ レプリカ上で個別に中断されたセカンダリ データベースを再開するには、セカンダリ レプリカをホストするサーバー インスタンスに接続し、そこでデータベースを再開します。  
  
     同期コミット モードでは、データベースの状態が SYNCHRONIZING に変わります。 他のデータベースが現在中断されていない場合は、レプリカの状態も SYNCHRONIZING に変わります。  
  
     詳細については、このトピックの「 [可用性データベースの再開 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/resume-an-availability-database-sql-server.md)の可用性データベースを中断できます。  
  
## <a name="database-states"></a>データベースの状態  
 セカンダリ データベースを可用性グループに参加させると、ローカル セカンダリ レプリカのセカンダリ データベースの状態が RESTORING から ONLINE に変わります。 セカンダリ データベースを可用性グループから削除すると、その状態はローカル セカンダリ レプリカによって RESTORING に戻ります。 これにより、プライマリ データベースからの後続のログ バックアップをそのセカンダリ データベースに適用できます。  
  
## <a name="restrictions"></a>制限  
 トランザクションとバッチの外で ALTER DATABASE ステートメントを実行します。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 データベースに対する ALTER 権限が必要です。 データベースを可用性グループに参加させるには、メンバーシップが必要です、 **db_owner**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、セカンダリ データベース `AccountsDb1` を、`AccountsAG` 可用性グループのローカル セカンダリ レプリカに参加させます。  
  
```  
ALTER DATABASE AccountsDb1 SET HADR AVAILABILITY GROUP = AccountsAG;  
```  
  
> [!NOTE]  
>  コンテキストで使用するこの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを確認するには、「[可用性グループの作成 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [可用性グループ &#40;Transact SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40; の概要SQL Server &#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) [AlwaysOn 可用性グループの構成 &#40; のトラブルシューティングSQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md) 
  
  
