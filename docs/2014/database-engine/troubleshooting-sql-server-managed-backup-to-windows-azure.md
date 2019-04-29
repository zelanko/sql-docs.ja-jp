---
title: Windows Azure へのバックアップを管理する SQL Server のトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: a34d35b0-48eb-4ed1-9f19-ea14754650da
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd68f6f8bcb83bfbc980be0809e12141403e4012
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842579"
---
# <a name="troubleshooting-sql-server-managed--backup-to-windows-azure"></a>Windows Azure への SQL Server マネージド バックアップのトラブルシューティング
  このトピックでは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の操作中に発生する可能性があるエラーのトラブルシューティングに使用できるツールとタスクについて説明します。  
  
## <a name="overview"></a>概要  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]には、組み込みのチェックとトラブルシューティング機能が用意されているため、多くの場合、内部エラーは [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)] プロセス自体によって対処されます。  
  
 このような 1 つのケースの例は、ログの中断が生じるバックアップ ファイルの削除のチェーンに影響を与えるの回復性 -[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]ログ チェーンの中断が識別され、すぐに実行するバックアップをスケジュールします。 ただし、状態を監視して、手動による介入を必要とするエラーには対処することをお勧めします。  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、システム ストアド プロシージャ、システム ビュー、および拡張イベントを使用して、イベントとエラーがログに記録されます。 システム ビューとストアド プロシージャでは、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の構成情報、バックアップの状態、定期的なバックアップ、さらに、拡張イベントによってキャプチャされたエラーが提供されます。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]は、拡張イベントを使用して、トラブルシューティングに使用するエラーをキャプチャします。 SQL Server Smart Admin ポリシーは、イベントのログ記録に加え、正常性状態も提供します。正常性状態は、通知またはエラーや問題を示すために電子メール通知ジョブで使用されます。 詳細については、次を参照してください。[モニター SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)します。  
  
 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、Windows Azure ストレージの手動バックアップ (SQL Server Backup to URL) で使用されるものと同じログ記録が使用されます。 詳細については、Backup to URL 関連の問題は、トラブルシューティングのセクションを参照してください[SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング。](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
### <a name="general-troubleshooting-steps"></a>一般的なトラブルシューティング手順  
  
1.  電子メール通知を有効にして、エラーと警告に関する電子メールの受信を開始します。  
  
     また、定期的に `smart_admin.fn_get_health_status` を実行して集計されたエラーおよび数を確認することもできます。 たとえば、`number_of_invalid_credential_errors` は、スマート バックアップでバックアップを試行して "無効な資格情報" エラーが発生した回数です。 `Number_of_backup_loops` と `number_of_retention_loops` はエラーではなく、バックアップ スレッドと保有期間スレッドがデータベースの一覧をスキャンした回数を示します。 通常、@begin_timeと@end_timeが指定されていない場合、関数が最後の 30 分からの情報を表示し、これら 2 つの列の値が 0 以外が通常表示します。 これらの値がゼロの場合は、システムがオーバーロードされたかシステムが応答していないことを意味します。 詳細については、次を参照してください。**システムに関する問題のトラブルシューティング**このトピックで後述します。  
  
2.  拡張イベント ログを確認して、エラーと関連するその他のイベントの詳細を理解します。  
  
3.  ログの情報を使用して、問題を解決します。  システムに関する問題またはエラーが発生した場合は、サービスまたは SQL Server エージェントの再起動が必要になることがあります。  
  
### <a name="common-causes-of-errors"></a>エラーの一般的な原因  
 エラーの一般的な原因の一覧を次に示します。  
  
1.  **SQL 資格情報の変更:** 資格情報の名前で使用されている場合[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が変更または削除すると、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]バックアップを実行することはできません。 変更は [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の構成設定に適用する必要があります。  
  
2.  **ストレージ アクセス キーの値の変更:** Windows Azure アカウントのストレージ キーの値が変更されますが、SQL 資格情報は、新しい値を更新しない場合[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]ストレージへの認証時に失敗し、このアカウントを使用するように構成データベースをバックアップします。  
  
3.  **Windows Azure ストレージ アカウントの変更:** 削除または SQL 資格情報に対応する変更が発生せず、ストレージ アカウントを名前変更[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が失敗し、バックアップは実行されません。 ストレージ アカウントを削除する場合は、有効なストレージ アカウント情報を使用してデータベースを再構成してください。 ストレージ アカウントの名前を変更したり、キー値を変更したりする場合は、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]で使用されている SQL 資格情報にこれらの変更が反映されるようにしてください。  
  
4.  **データベースのプロパティの変更:** 復旧モデルへの変更または名前を変更するには、バックアップが失敗する可能性があります。  
  
5.  **復旧モデルの変更:** データベースの復旧モデルから完全または一括ログは、単純に変更したかどうか、バックアップは停止され、およびで、データベースがスキップされます[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]します。 詳細については、次を参照してください[SQL Server Managed Backup to Windows Azure:。相互運用性と共存](../../2014/database-engine/sql-server-managed-backup-to-windows-azure-interoperability-and-coexistence.md)  
  
### <a name="most-common-error-messages-and-solutions"></a>最も一般的なエラー メッセージと解決方法  
  
1.  **エラーを有効にするかを構成するときに[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]:**  
  
     エラー:"ストレージ URL にアクセスできませんでした.有効な SQL 資格情報を指定してください..."。これと他の同様のエラーを参照する SQL 資格情報を表示があります。  このような場合は、指定した SQL 資格情報とも SQL 資格情報のストレージ アカウント名、およびストレージ アクセス キーに格納されている情報の名前を確認し、それらが最新かつ有効なことかどうかを確認します。  
  
     エラー:"... システム データベースであるため... データベースを構成することはできません"。有効にしようとする場合、このエラーが表示されます[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]システム データベースです。  [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]では、システム データベースのバックアップがサポートされません。  システム データベースのバックアップを構成するには、メンテナンス プランなどの別の SQL Server バックアップ テクノロジを使用してください。  
  
     エラー:"しています."... 保有期間を指定します。いずれかが指定されていない場合、データベースまたはインスタンスの保有期間、最初にこれらの値を構成する際、保有期間に関するのエラーが発生する可能性があります。 また、1 ～ 30 の数値以外の値を指定した場合にもエラーが表示されることがあります。 保有期間に許可される値は 1 ～ 30 の数値です。  
  
2.  **電子メール通知エラー:**  
  
     エラー:「データベース メールが有効になっていません…」- 電子メールによる通知を有効にしたが、データベース メールがインスタンスで構成されていない場合、このエラーが表示されます。 [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]の正常性状態の通知を受信できるように、インスタンス上のデータベース メールを構成する必要があります。 データベース メールを有効にする方法については、次を参照してください。[データベース メールの構成](../relational-databases/database-mail/configure-database-mail.md)します。 また、通知にデータベース メールを使用するには、SQL Server エージェントを有効にする必要があります。 詳細については、次を参照してください。[開始する前に](../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md#BeforeYouBegin)します。  
  
     電子メール通知に関連するエラー番号を次に示します。  
  
    -   エラー番号:45209  
  
    -   エラー番号:45210  
  
    -   エラー番号:45211  
  
3.  **接続エラー:**  
  
    -   **SQL 接続に関連するエラー:** SQL Server インスタンスへの接続の問題がある場合に、これらのエラーが発生します。 拡張イベントは、管理チャネルを介してこの種のエラーを公開します。 次の 2 つの拡張イベントにより、この種の接続の問題に関連するエラーを確認できます。  
  
         event_type が SqlError である FileRetentionAdminXEvent。 このエラーの詳細については、このイベントの error_code、error_message、および stack_trace を確認してください。 Error_code は SqlException のエラー番号です。  
  
         次のメッセージまたはメッセージ プレフィックスが含まれた SmartBackupAdminXevent。  
  
         *"既定の設定を Windows Azure に SQL Server マネージ バックアップを構成するときに内部エラーが発生しました。 のインスタンス。エラーが一時的なである。"*  
  
         *"SQL Server と接続に問題が発生して可能性があります。現在のイテレーションでデータベースをスキップします。"*  
  
         *"クエリ ログの使用方法に関する情報が失敗しました。これは一時的なエラーである可能性があります。現在のイテレーションでデータベースをスキップします。"*  
  
         *"SSMBackup2WA エージェントのメタデータの読み込み中に発生した SQL 例外。これは一時的なエラーである可能性があります。操作は再試行されます。"*  
  
         *"SSMBackup2WA は、SQL 例外... 中が発生しました"*  
  
    -   **ストレージ アカウントへの接続エラー:**  
  
         event_type が XstoreError である FileRetentionAdminXEvent では、ストレージ例外が報告されます。 このエラーの詳細については、このイベントの error_message と stack_trace を確認してください。  
  
         SQL Server マネージド バックアップでは基になる Backup to URL テクノロジを使用するため、ストレージ接続に関連するエラーは両方の機能に適用されます。 トラブルシューティングの手順の詳細については、次を参照してください。**トラブルシューティングのセクション**の、 [SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング](../relational-databases/backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)記事。  
  
### <a name="troubleshooting-system-issues"></a>システムに関する問題のトラブルシューティング  
 システム (SQL Server、SQL Server エージェント) で問題が発生した場合のシナリオと、その場合に [!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が受ける影響を次に示します。  
  
-   **Sqlservr.exe の応答を停止または動作を停止[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が実行されています。** SQL エージェントが正常にシャット ダウン、SQL Server が動作しなくなった場合[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]SQL Agent.out ファイルに停止し、イベントを記録することもできます。  
  
     SQL Server が応答を停止した場合は、イベント ログが管理チャネルに記録されます。  イベント ログの例を次に示します。  
  
     *Sql エラー (エンジン応答していないか、sqlException を取得します。SqlException:*   
     *エラー コード、メッセージおよびスタック トレースがような追加の情報と共に、管理者チャネル xevent で表示されます。*   
    *"SQL Server と接続に問題が発生して可能性があります。現在のイテレーションでデータベースをスキップしています"*  
  
-   **SQL エージェントが応答を停止または動作を停止[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]が実行されています。**  
  
     SQL エージェントが動作を停止すると、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]も停止され、イベント ログが管理チャネルに記録されます。 これは、SQL Server が応答を停止した場合のシナリオに似ています。  
  
     SQL エージェントが応答を停止した場合、[!INCLUDE[ss_smartbackup](../includes/ss-smartbackup-md.md)]はバックアップ操作を継続できず、イベント ログが管理チャネルに記録されます。 イベント ログの例を次に示します。  
  
     *ジョブを停止: xevent 管理チャネルを参照してください。*   
    *"進行状況の更新での SQL Server から受信していません以上の"+ Constants.DBBackupInfoMsgMaxWaitTime +"データベースのバックアップの時間です。 SSM クラウド バックアップは引き続き待機します。"*  
  
 電子メール通知を有効にした場合を含む通知を受信は**バックアップ ループの数**と**保有期間のループの数**します。 これらの列の一方または両方について、通知に示されている値がゼロであれば、システムが応答していない可能性があります。  
  
> [!WARNING]  
>  レポートの結果を生成する内部プロセスは、エンジンの診断ログが SQL エージェント エラー ログと同じ場所に存在することを想定します。SQL エージェント エラー ログは、既定では SQL Server インスタンスのエラー ログと同じフォルダーにあります。 エンジンの診断ログを、SQL エージェント エラー ログとは異なる場所に移動した場合は、システムはスマート バックアップの診断ログを見つけることができなくなるため、電子メール通知内のレポートが正しくなくなる可能性があります。 たとえばの値を表示可能性があります**0**すべてのフィールドに、バックアップ ループの数と保有期間のループの数を含め、報告されます。 この場合、診断ログを別の場所に移動した状況で、システムが応答しなくなるわけではなく、システムがログを見つけられなくなることを意味します。 最初に、診断ログと SQL エージェント エラー ログが同じ場所にあることを確認してください。 使用することができます、診断ログの現在の場所を確認する[sys.dm_os_server_diagnostics_log_configurations](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-server-diagnostics-log-configurations)します。 `path`列診断ログは、エンジンの現在の場所を返します。  これは、SQL エージェント エラー ログと同じフォルダーに存在する必要があります。 `dbo.sp_get_sqlagent_properties` ストアド プロシージャを使用して、SQL エージェント エラー ログのパスを取得できます。  
  
 拡張イベント ログでエラーの詳細を確認してください。 エラーを修正するか、SQL Server エージェントを再起動して状況を修正します。  
  
  
