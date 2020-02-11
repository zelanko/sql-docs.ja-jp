---
title: データベースが破損したときのトランザクション ログのバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server], damaged
- backing up [SQL Server]. damaged database
- transaction log backups [SQL Server], damaged databases
ms.assetid: 9b8873cc-df54-4336-ab9b-8f525132c2b0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69e887cc2a8f35710a0c7c910e0e912d6a4a0a61
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62922847"
---
# <a name="back-up-the-transaction-log-when-the-database-is-damaged-sql-server"></a>データベースが破損したときのトランザクション ログのバックアップ (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、データベースが損傷しているときにトランザクション ログをバックアップする方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Recommendations (推奨事項)](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **データベースが破損したときにトランザクションログをバックアップするために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   データベースで完全復旧モデルまたは一括ログ復旧モデルを使用している場合は、通常、データベースの復元を開始する前に、ログの末尾をバックアップする必要があります。 また、ログ配布構成をフェールオーバーする前に、プライマリ データベースのログの末尾もバックアップする必要があります。 データベースを復旧する前にログ末尾のバックアップを最後のログ バックアップとして復元すると、障害発生後の作業損失を防ぐことができます。 ログ末尾のバックアップの詳細については、「[ログ末尾のバックアップ &#40;SQL Server&#41;](tail-log-backups-sql-server.md)」をご覧ください。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。  
  
 バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が必要です。 ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)では、ファイル アクセスの権限は確認 されません 。 バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-back-up-the-tail-of-the-transaction-log"></a>トランザクション ログの末尾をバックアップするには  
  
1.  の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]適切なインスタンスに接続した後、オブジェクトエクスプローラーで、サーバー名をクリックしてサーバーツリーを展開します。  
  
2.  [**データベース] を展開し**、データベースに応じて、ユーザーデータベースを選択するか、[**システムデータベース**] を展開してシステムデータベースを選択します。  
  
3.  データベースを右クリックし、**[タスク]** をポイントして、**[バックアップ]** をクリックします。 
  **[データベースのバックアップ]** ダイアログ ボックスが表示されます。  
  
4.  
  **[データベース]** ボックスに、適切なデータベース名が表示されていることを確認します。 必要に応じて、このボックスの一覧から別のデータベースを選択することもできます。  
  
5.  復旧モデルが **[FULL]** または **[BULK_LOGGED]** であることを確認します。  
  
6.  
  **[バックアップの種類]** ボックスの一覧で、 **[トランザクション ログ]** を選択します。  
  
7.  
  **[バックアップのみコピーする]** はオフのままにしておきます。  
  
8.  
  **[バックアップ セット]** で、表示された既定のバックアップ セット名をそのまま使用するか、または **[名前]** ボックスに別のバックアップ セット名を入力します。  
  
9. 
  **[説明]** ボックスに、ログ末尾のバックアップの説明を入力します。  
  
10. バックアップ セットの有効期限を指定します。  
  
    -   特定の日数が経過した後、バックアップ セットを有効期限切れにするには、**[期間指定]** (既定のオプション) をクリックし、日数を入力します。セットの作成後、この日数が経過すると、セットは有効期限切れになります。 0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。  
  
         既定値は、[**サーバーのプロパティ**] ダイアログボックス ([**データベースの設定**] ページ) の [**バックアップメディアの既定の保有期間 (日)** ] オプションで設定されています。 このダイアログ ボックスを開くには、オブジェクト エクスプローラーでサーバー名を右クリックし、[プロパティ] をクリックして、 **[データベースの設定]** ページを選択します。  
  
    -   バックアップ セットを特定の日付で有効期限切れにするには、**[日時指定]** をクリックし、セットを有効期限切れにする日付を入力します。  
  
11. 
  **[ディスク]** または **[テープ]** をクリックして、バックアップ先を選択します。 1 つのメディア セットを含んでいる最大 64 個のディスク ドライブまたはテープ ドライブのパスを選択するには、 **[追加]** をクリックします。 選択したパスは、 **[バックアップ先]** ボックスの一覧に表示されます。  
  
     バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。 バックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。  
  
12. 
  **[オプション]** ページで、次のいずれかをクリックして **[メディアに上書きします]** オプションを選択します。  
  
    -   **既存のメディアセットへのバックアップ**  
  
         このオプションでは、 **[既存のバックアップ セットに追加する]** または **[既存のすべてのバックアップ セットを上書きする]** をクリックします。  
  
         必要に応じて、 **[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスをオンにします。これにより、バックアップ操作で、メディア セットとバックアップ セットの有効期限が切れる日付と時刻の確認が行われます。  
  
         必要に応じて、 **[メディア セット名]** ボックスに名前を入力します。 名前を指定しなかった場合、空の名前でメディア セットが作成されます。 メディア セット名を指定した場合は、メディア (テープまたはディスク) の実際の名前がここで入力した名前と一致しているかどうかが確認されます。  
  
         メディア名を指定せずに、このチェック ボックスをオンにしてこのメディアを確認するよう指定した場合は、実際のメディア名も空でないとエラーになります。  
  
    -   **新しいメディアセットにバックアップし、既存のすべてのバックアップセットを消去する**  
  
         このオプションでは、 **[新しいメディア セット名]** ボックスに名前を入力し、必要に応じて **[新しいメディア セットの説明]** ボックスにメディア セットの説明を入力します。  
  
     メディア セット オプションの詳細については、「[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」 を参照してください。  
  
13. [**信頼性**] セクションで、必要に応じて次のチェックボックスをオンにします。  
  
    -   **完了時にバックアップを確認**します。  
  
    -   **メディアに書き込む前にチェックサムを実行**します。  
  
    -   **チェックサムエラーのまま続行する**  
  
     チェックサムの詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md)」を参照してください。  
  
14. 
  **[トランザクション ログ]** セクションで、 **[ログの末尾をバックアップし、データベースを復元中の状態にしておく]** をオンにします。  
  
     これは、次の [BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントを指定することと同じです。  
  
     `BACKUP LOG <database_name> TO <backup_device> WITH NORECOVERY`  
  
    > [!IMPORTANT]  
    >  復元時には、[データベースの復元] ダイアログ ボックスに、ログ末尾のバックアップの種類が **[トランザクション ログ (コピーのみ)]** として表示されます。  
  
15. 
  **[全般]** ページの **[バックアップ先]** セクションで、テープ ドライブにバックアップするように指定した場合は、 **[バックアップ後にテープをアンロードする]** チェック ボックスがアクティブになります。 このオプションをオンにすると、 **[アンロードの前にテープを巻き戻す]** オプションがアクティブになります。  
  
16. [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)]以降では、[バックアップの圧縮](backup-compression-sql-server.md)がサポートされます。 既定では、バックアップが圧縮されるかどうかは、**[バックアップ圧縮の既定]** サーバー構成オプションの値によって決まります。 ただし、現在のサーバー レベルの既定値に関係なく、**[バックアップを圧縮する]** チェック ボックスをオンにしてバックアップを圧縮することも、**[バックアップを圧縮しない]** チェック ボックスをオンにして圧縮を無効にすることもできます。  
  
     **現在のバックアップの圧縮の既定値を表示するには**  
  
    -   [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-backup-of-the-currently-active-transaction-log"></a>現在アクティブなトランザクション ログのバックアップを作成するには  
  
1.  BACKUP LOG ステートメントを実行し、現在アクティブなトランザクション ログをバックアップします。このとき、次の指定を行います。  
  
    -   バックアップするトランザクション ログが属しているデータベースの名前。  
  
    -   トランザクション ログ バックアップが書き込まれるバックアップ デバイス。  
  
    -   NO_TRUNCATE 句。  
  
         この句を使用すると、データベースにアクセスできない場合でも、トランザクション ログ ファイルにアクセスでき、損傷していなければ、トランザクション ログのアクティブな部分をバックアップできます。  
  
###  <a name="TsqlExample"></a>例 (Transact-sql)  
  
> [!NOTE]  
>  この例では、単純復旧モデルを使用する [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]を使用しています。 ただし、ログ バックアップを可能にするために、データベースの完全バックアップを行う前に、データベースが完全復旧モデルを使用するように設定されています。 詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。  
  
 この例では、データベースが破損していてアクセスできないときでも、トランザクション ログ ファイルが破損しておらずアクセスできる場合は、現在アクティブなトランザクション ログをバックアップします。  
  
```scr  
BACKUP LOG AdventureWorks2012  
   TO MyAdvWorks_FullRM_log1  
   WITH NO_TRUNCATE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [トランザクションログバックアップを復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)   
 [SQL Server データベースを &#40;完全復旧モデルの特定の時点に復元する&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)   
 [[データベースのバックアップ &#40;バックアップオプション] ページ&#41;](back-up-database-backup-options-page.md)   
 [データベースのバックアップ &#40;[全般] ページ&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)   
 [トランザクションログバックアップの適用 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [Transact-sql&#41;のバックアップ &#40;](/sql/t-sql/statements/backup-transact-sql)   
 [ファイル復元 &#40;単純復旧モデル&#41;](file-restores-simple-recovery-model.md)   
 [完全復旧モデルのファイル復元 &#40;&#41;](file-restores-full-recovery-model.md)  
  
  
