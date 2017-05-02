---
title: "データベース チェックポイント (SQL Server) | Microsoft Docs"
ms.date: 09/23/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automatic checkpoints
- transaction logs [SQL Server], checkpoints
- logs [SQL Server], active
- pages [SQL Server], dirty
- MinLSN
- checkpoints [SQL Server]
- pages [SQL Server], flushing
- dirty pages
- transaction logs [SQL Server], active logs
- recovery interval option [SQL Server]
- buffer cache [SQL Server]
- logs [SQL Server], checkpoints
- Minimum Recovery LSN
- flushing pages
- active logs
ms.assetid: 98a80238-7409-4708-8a7d-5defd9957185
caps.latest.revision: 74
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9c46ed7578abfaacec840270f45a132cc438a82c
ms.lasthandoff: 04/11/2017

---
# <a name="database-checkpoints-sql-server"></a>データベース チェックポイント (SQL Server)
 *チェックポイント* によって、予期しないシャットダウンやクラッシュの後の復旧中に、ログに格納されている変更を [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] が適用するための最適なポイントが作成されます。  
 
  
##  <a name="Overview"></a> 概要   
パフォーマンス向上のため、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では、メモリ (バッファー キャッシュ) にあるデータベース ページが変更されるようになり、ページが変更されるたびにディスクに書き込まれることはなくなりました。 また、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では定期的に各データベースにチェックポイントが発行されます。 *チェックポイント* では、現在メモリにある修正ページ (つまり *ダーティ ページ*) とトランザクション ログ情報がメモリからディスクに書き込まれ、トランザクション ログの情報も記録されます。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] では、自動、間接、手動、および内部といったチェックポイントの種類がサポートされています。 次の表は、 **チェックポイント**の種類をまとめたものです。
  
|名前|[!INCLUDE[tsql](../../includes/tsql-md.md)] インターフェイス|説明|  
|----------|----------------------------------|-----------------|  
|自動|EXEC sp_configure **'**recovery interval**','***seconds***'**|**recovery interval** サーバー構成オプションに指定された期限に合わせて、バックグラウンドで自動的に発行されます。 自動チェックポイントは、最後まで実行されます。  自動チェックポイントは、未処理の書き込み数と、50 ミリ秒を超える書き込み待機時間の上昇を [!INCLUDE[ssDE](../../includes/ssde-md.md)] が検出したかどうかに応じて調整されます。<br /><br /> 詳細については、「 [recovery interval サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)」を参照してください。|  
|間接|ALTER DATABASE … SET TARGET_RECOVERY_TIME **=***target_recovery_time* { SECONDS &#124; MINUTES }|所定のデータベースのユーザーが指定したターゲット復旧時間に合わせて、バック グラウンドで発行されます。 [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]より、既定値は 1 分です。 旧バージョンの既定値は 0 です。これは、データベースが自動チェックポイントを使用することを示し、その頻度はサーバー インスタンスの復旧間隔の設定に依存します。<br /><br /> 詳細については、「 [データベースのターゲットの復旧時間の変更 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)」を参照してください。|  
|手動|CHECKPOINT [ *checkpoint_duration* ]|[!INCLUDE[tsql](../../includes/tsql-md.md)] CHECKPOINT コマンドを実行すると発行されます。 接続している現在のデータベースで手動チェックポイントが作成されます。 既定では、手動のチェックポイントは最後まで実行されます。 調整は自動チェックポイントの場合と同様に行われます。  必要に応じて、 *checkpoint_duration* パラメーターを使用し、チェックポイントを完了するのに必要な時間を秒単位で指定します。<br /><br /> 詳細については、「 [CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)」を参照してください。|  
|Internal|[なし] :|ディスク イメージがログの現在の状態と一致することを保証するために、バックアップやデータベース スナップショット作成など、さまざまなサーバー操作によって発行されます。|  
  
>[!NOTE]
> 一部の種類のチェックポイントでは、データベース管理者が **-k** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の詳細設定オプションを使用して、I/O サブシステムのスループットに基づいてチェックポイントの I/O 動作を調整できます。 **-k** 設定オプションは、自動チェックポイント、手動チェックポイント、および内部チェックポイントに適用されます (手動チェックポイントと内部チェックポイントは通常は調整されません)。  
  
 自動チェックポイント、手動チェックポイント、および内部チェックポイントでは、データベース復旧中にロールフォワードする必要があるのは、最新チェックポイントの後で行われた修正のみです。 これにより、データベースの復旧にかかる時間が短縮されます。  
  
>[!IMPORTANT]
> 実行時間の長い、コミットされていないトランザクションがあると、すべての種類のチェックポイントで復旧時間が長くなります。  
  
  
##  <a name="InteractionBwnSettings"></a> TARGET_RECOVERY_TIME オプションと 'recovery interval' オプションの相互作用  
 次の表は、サーバー全体の **sp_configure'**recovery interval**'** 設定とデータベース固有の ALTER DATABASE … TARGET_RECOVERY_TIME 設定の相互作用をまとめたものです。  
  
|target_recovery_time|'recovery interval'|使用されるチェックポイントの種類|  
|----------------------------|-------------------------|-----------------------------|  
|0|0|ターゲット復旧間隔が 1 分の自動チェックポイント|  
|0|>0|ターゲット復旧間隔が **sp_configurerecovery interval** オプションのユーザー定義設定によって指定されている自動チェックポイント。|  
|>0|該当なし。|復旧時間が TARGET_RECOVERY_TIME 設定 (秒単位) によって設定されている間接チェックポイント ターゲット|  
  
##  <a name="AutomaticChkpt"></a> 自動チェックポイント  
 自動チェックポイントが発生するのは、ログ レコード数が、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] recovery interval **サーバー構成オプションで指定された時間内に処理できると** が推定した数に達したときです。 
 
 ユーザー定義のターゲット復旧時間が設定されていないすべてのデータベースでは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によって自動チェックポイントが生成されます。 自動チェックポイントの作成回数は、 **recovery interval** 詳細サーバー構成オプションに応じて異なります (これは、システムの再起動時に、所定のサーバー インスタンスがデータベースの復旧にかけられる最大時間を指定します)。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は、復旧間隔内に処理できるログ レコードの最大数を推定します。 自動チェックポイントを使用するデータベースのログ レコードが最大数に達すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] によってデータベースでチェックポイントが発行されます。 
 
 自動チェックポイントの作成間隔は **大幅に** 変わります。 相当量のトランザクション ワークロードがあるデータベースでは、主に読み取り専用操作で使用されるデータベースよりもチェックポイントの作成回数が多くなります。 単純復旧モデルの場合、ログが全体の 70% に達すると自動チェックポイントもキューに登録されます。  
  
単純復旧モデルでは、ログ トランザクションが何かの要因によって遅れていない限り、自動チェックポイントにより、トランザクション ログの未使用のセクションが切り捨てられます。 一方、完全復旧モデルおよび一括ログ復旧モデルでは、ログ バックアップ チェーンが確立されると、自動チェックポイントによるログの切り捨ては行われなくなります。 詳細については、「 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)」を参照してください。  
  
 システム障害の後で所定のデータベースの復旧に必要な時間は、障害発生時点でのダーティ ページを再実行するために必要なランダム I/O の容量に大きく依存します。 つまり、 **recovery interval** の設定は信頼できません。 正確な復旧間隔がわかりません。 さらに、自動チェックポイントの進行中に、データの一般的な I/O アクティビティが急に著しく増加します。  
  
 
###  <a name="PerformanceImpact"></a> 復旧のパフォーマンスに対する復旧間隔の影響  
 短いトランザクションを使用するオンライン トランザクション処理 (OLTP) システムでは、 **recovery interval** の設定が復旧にかかる時間を決定する主な要因になります。 ただし、 **recovery interval** オプションは、実行時間が長いトランザクションを元に戻すために必要な時間には影響しません。 実行時間が長いトランザクションが行われたデータベースの復旧は、 **recovery interval** オプションで指定された時間よりも長くかかることがあります。 
 
 たとえば、実行時間の長いトランザクションが 2 時間かけて更新した後にサーバー インスタンスが使用不能になった場合、長いトランザクションを復旧することになるので、実際の復旧時間は **recovery interval** 値よりもはるかに長くなります。 実行時間が長いトランザクションの復旧時間への影響の詳細については、「 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)」を参照してください。  
  
 通常は、既定値によって復旧の最適なパフォーマンスが得られます。 ただし、次のような状況では recovery interval を変更するとパフォーマンスが向上する可能性があります。  
  
-   実行時間の長いトランザクションがロールバックされていないのに、復旧にかかる時間が常に 1 分を超える場合  
  
-   チェックポイントの回数が多いためにデータベースのパフォーマンスが損なわれていると判断できる場合  
  
 **recovery interval** 設定を長くする場合には、少しずつ値を増やして、そのたびに復旧のパフォーマンスへの影響を評価することをお勧めします。 **recovery interval** の設定を長くすると、完了するまでに何倍もの時間がかかるため、この方法で進めることが重要です。 たとえば、 **recovery interval** の値を 10 分に変更すると、 **recovery interval** が既定値の 1 分に設定された場合の約 10 倍の時間がかかります。  
  
  
##  <a name="IndirectChkpt"></a> 間接チェックポイント  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]に導入された間接チェックポイントは、自動チェックポイントの代わりに使用できる、構成可能なデータベース レベルのチェックポイントです。 間接チェックポイントでは、自動チェックポイントに比べて、システム障害時の復旧時間が短く、予測可能です。 間接チェックポイントには次の利点があります。  
  
-   間接チェックポイントが構成されたデータベースでオンライン トランザクション ワークロードが生じると、パフォーマンスが低下することがあります。 間接チェックポイントは、ターゲットの復旧時間内でデータベースの回復が完了するように、ダーティ ページの数が特定のしきい値を下回るようにします。 

復旧間隔構成オプションは、ダーティ ページ数を使用する間接チェックポイントとは異なり、トランザクション数を使用して復旧時間を決定します。 DML 操作の受信数が多いデータベースで間接チェックポイントが有効な場合、バックグラウンド ライターは積極的にディスクにダーティ バッファーのフラッシュを開始し、回復を実行するのに必要な時間をデータベースのターゲット復旧時間内にすることができます。 これにより、ディスクのサブシステムが I/O のしきい値よりも高い動作をするかまたはその値に近づいた場合、パフォーマンス ボトルネックの原因となる追加の I/O アクティビティが特定のシステムで発生する可能性があります。  
  
-   間接チェックポイントを使用すると、REDO 時のランダム I/O のコストを計算に入れて、データベースの復旧時間を確実に制御できます。 このため、所定のデータベースで、復旧時にサーバー インスタンスが上限内にとどまることができます (実行時間の長いトランザクションによって過度の UNDO 回数が生じる場合以外)。  
  
-   間接チェックポイントでは、ディスクへのダーティ ページの書き込みがバックグラウンドで続けられるため、チェックポイントに関連する I/O の急上昇が少なくなります。  
  
 ただし、間接チェックポイントが構成されたデータベースでオンライン トランザクション ワークロードが生じると、パフォーマンスが低下することがあります。 これは、間接チェックポイントで使用されるバックグラウンド ライターによって、サーバー インスタンスの合計書き込みロードが増える場合があるためです。  
 
 > [!IMPORTANT]
 > 間接チェックポイントは、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] で作成された新しいデータベースの既定の動作です。 インプレース アップグレードまたは以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から復元されたデータベースは、間接チェックポイントを使用するように明示的に変更しない限り、以前の自動チェックポイントを使用します。
  
  
##  <a name="EventsCausingChkpt"></a> 内部チェックポイント  
 内部チェックポイントは、ディスク イメージがログの現在の状態と一致することを保証するために、さまざまなサーバー コンポーネントによって生成されます。 内部チェックポイントは、次のイベントに応答して生成されます。  
  
-   ALTER DATABASE を使用して、データベース ファイルが追加または削除された場合。  
  
-   データベースのバックアップが作成された場合。  
  
-   DBCC CHECK で明示的または内部的に、データベース スナップショットが作成された場合。  
  
-   データベースのシャットダウンが必要な動作が実行された場合。 たとえば、AUTO_CLOSE が ON に設定されていて、データベースへの最後のユーザー接続が終了した場合、またはデータベースの再起動が必要なデータベース オプションが変更された場合です。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) サービスを停止することによって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが停止します。 どちらの場合でも、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの各データベースでチェックポイントが作成されます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンス (FCI) がオフラインになった場合。  
  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **サーバー インスタンスで復旧間隔を変更するには**  
  
-   [recovery interval サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)  
  
 **データベースで間接チェックポイントを構成するには**  
  
-   [データベースのターゲットの復旧時間の変更 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md)  
  
 **データベースで手動チェックポイントを発行するには**  
  
-   [CHECKPOINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)  

  
## <a name="see-also"></a>参照  
 - [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md) 
 -   [トランザクション ログの物理アーキテクチャ](http://technet.microsoft.com/library/ms179355.aspx) ( [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] オンライン ブックからですが、適用可能です)  
  
  

