---
title: "データベースの完全バックアップの作成 (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
caps.latest.revision: 63
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: a5f180c837af757fd5a8df7f356b8c644916612f
ms.contentlocale: ja-jp
ms.lasthandoff: 10/11/2017

---
# <a name="create-a-full-database-backup-sql-server"></a>データベースの完全バックアップの作成 (SQL Server)

 > SQL Server 2014 の場合は、「[データベースの完全バックアップの作成 (SQL Server)](https://msdn.microsoft.com/en-US/library/ms187510(SQL.120).aspx)」を参照してください。

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、または PowerShell を使用して、データベースの完全バックアップを作成する方法について説明します。  
  
>  Azure BLOB ストレージ サービスへの SQL Server のバックアップについては、「[Microsoft Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」および「[SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md)」を参照してください。  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備 
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。  
  
-   新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって作成されたバックアップは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では復元できません。  
  
-   バックアップの概要、詳細、概念およびタスクについて、「 [バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md) 」を参照してから先に進んでください。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   データベース サイズが大きくなると、データベースの完全バックアップにかかる時間は長くなり、必要な記憶領域も増加します。 大規模なデータベースでは、[データベースの差分バックアップ](../../relational-databases/backup-restore/differential-backups-sql-server.md) を使用してデータベースの完全バックアップを補完することを検討してください。 詳細については、「 [SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md)」を参照してください。  
  
-   データベースの完全バックアップのサイズは、 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) システム ストアド プロシージャを使用して推計します。  
  
-   既定では、バックアップ操作が成功するたびに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにエントリが 1 つ追加されます。 頻繁にバックアップすると、これらの成功メッセージがすぐに蓄積され、エラー ログが大きくなります。 そのために、他のメッセージを探すのが困難になることがあります。 そのような場合、これらのエントリに依存するスクリプトがなければ、トレース フラグ 3226 を使用することによってこれらのバックアップ ログ エントリを除外できます。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」を参照してください。  
  
###  <a name="Security"></a> セキュリティ  
 データベースをバックアップすると、TRUSTWORTHY は OFF に設定されます。 TRUSTWORTHY を ON に設定する方法については「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)」を参照してください。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、バックアップの作成での **PASSWORD** および **MEDIAPASSWORD** オプションが廃止されました。 パスワード付きで作成されたバックアップを復元することは、引き続き可能です。  
  
####  <a name="Permissions"></a> 権限  
 BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。  
  
 バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が **必要** です。 ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)では、ファイル アクセスの権限は確認されません。 バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してバックアップ タスクを指定する場合、**[スクリプト]** ボタンをクリックしてスクリプトの保存先を選択することにより、対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](../../t-sql/statements/backup-transact-sql.md) スクリプトを生成できます。  
  
### <a name="back-up-a-database"></a>データベースをバックアップする  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]で適切な **[!INCLUDE[ssDEnoversion](../Token/ssDEnoversion_md.md)]**のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[データベース]**を展開し、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。  
  
3.  データベースを右クリックして **[タスク]**をポイントし、 **[バックアップ]**をクリックします。 **[データベースのバックアップ]** ダイアログ ボックスが表示されます。  

  #### <a name="general-page"></a>**[全般] ページ**
  
4.  **[データベース]** ボックスの一覧で、適切なデータベース名が表示されていることを確認します。 必要に応じて、このボックスの一覧から別のデータベースを選択することもできます。  
  
5.  **[復旧モデル]** テキスト ボックスは参照専用です。  どの復旧モデル (**[FULL]**、 **[BULK_LOGGED]**、 **[SIMPLE]**) でも、データベースのバックアップを実行できます。  
  
6.  **[バックアップの種類]** ボックスの一覧で、 **[完全]**を選択します。  
  
     データベースの完全バックアップを作成すると、データベースの差分バックアップを作成できるようになります。詳細については、「 [データベースの差分バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)」を参照してください。  
  
7.  必要であれば、 **[コピーのみのバックアップ]** チェック ボックスをオンにして、コピーのみのバックアップを作成することもできます。 *コピーのみのバックアップ*は、従来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップのシーケンスから独立した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップです。 詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)」を参照してください。  コピーのみのバックアップは、**[差分]** バックアップの種類には使用できません。  

8.  **[バックアップ コンポーネント]**では、 **[データベース]** ラジオ ボタンを選択します。  
  
9. **[バックアップ先]** セクションでは、 **[バックアップ先]** ドロップダウン リストを使用してバックアップ先を選びます。 新しいバックアップ オブジェクトやバックアップ先を追加するには、 **[追加]** をクリックします。
  
     バックアップ先を削除するには、バックアップ先を選択して **[削除]**をクリックします。 既存のバックアップ先の内容を表示するには、バックアップ先を選択して **[内容]**をクリックします。  

  #### <a name="media-options-page"></a>**[メディア オプション] ページ**  
10. メディア オプションを表示または選択するには、 **[ページの選択]** ペインの **[メディア オプション]** をクリックします。   
    
11. 次のいずれかをクリックして、 **[メディアに上書きします]** オプションを選択します。 

    > [!IMPORTANT]  
    >  **[全般]** ページでバックアップ先として **[URL]** を選択した場合、**[メディアを上書きする]** オプションは無効になります。 詳細については、「[[データベースのバックアップ] &#40;[メディア オプション] ページ&#41;](../../relational-databases/backup-restore/back-up-database-media-options-page.md)」を参照してください。  


  -   **[既存のメディア セットにバックアップする]**  
  
      > [!IMPORTANT]  
      >  暗号化を使用する場合は、このオプションを選択しないでください。 このオプションを選択すると、 **[バックアップ オプション]** ページの暗号化オプションが無効になります。 既存のバックアップ セットに追加するときには、暗号化はサポートされません。  
  
         このオプションでは、 **[既存のバックアップ セットに追加する]** または **[既存のすべてのバックアップ セットを上書きする]**をクリックします。 詳細については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。  
  
         必要に応じて、 **[メディア セット名とバックアップ セットの有効期限を確認する]** チェック ボックスをオンにします。これにより、バックアップ操作で、メディア セットとバックアップ セットの有効期限が切れる日付と時刻の確認が行われます。  
  
         必要に応じて、 **[メディア セット名]** ボックスに名前を入力します。 名前を指定しなかった場合、空の名前でメディア セットが作成されます。 メディア セット名を指定した場合は、メディア (テープまたはディスク) の実際の名前がここで入力した名前と一致しているかどうかが確認されます。  
  
-   **[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**  
  
    このオプションでは、 **[新しいメディア セット名]** ボックスに名前を入力し、必要に応じて **[新しいメディア セットの説明]** ボックスにメディア セットの説明を入力します。  
  
14. **[信頼性]** セクションで、必要に応じて以下のチェック ボックスをオンにします。  
  
    -   **[完了時にバックアップを検証する]**。  
  
    -   **[メディアに書き込む前にチェックサムを行う]**。  チェックサムの詳細については、「[バックアップ中および復元中に発生する可能性があるメディア エラー &#40;SQL Server&#41;](../../relational-databases/backup-restore/possible-media-errors-during-backup-and-restore-sql-server.md)」をご覧ください。  
    
    -   **[エラーのまま続行する]**。 

15. **[全般]** ページの **[バックアップの種類]** で、トランザクション ログをバックアップするように指定しなかった場合、 **[トランザクション ログ]** セクションは無効になっています。  
      
16. **[全般]** ページの **[バックアップ先]** セクションで、テープ ドライブにバックアップするように指定した場合、 **[テープ ドライブ]** セクションの **[バックアップ後にテープをアンロードする]** オプションが有効になります。 このオプションをオンにすると、 **[アンロードの前にテープを巻き戻す]** オプションがアクティブになります。   

  #### <a name="backup-options-page"></a>**[バックアップ オプション] ページ**  

17. バックアップ オプションを表示または選択するには、 **[ページの選択]** ペインの **[バックアップ オプション]** をクリックします。  
  
18. **[名前]** テキスト ボックスで、表示された既定のバックアップ セット名をそのまま使用するか、または別のバックアップ セット名を入力します。  
  
19. 必要に応じて、 **[説明]** ボックスにバックアップ セットの説明を入力します。  
  
20. バックアップ セットの有効期限と、有効期限が過ぎたデータを明示的に確認せずに上書きできるかどうかを指定します。  
  
    -   バックアップ セットが指定の日数後に期限切れになるようにするには、 **[期間指定]** (既定のオプション) をクリックし、セットを作成してからセットが期限切れになるまでの日数を入力します。 0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。  
  
         既定値は、 **[サーバーのプロパティ]** ダイアログ ボックス ([データベースの設定] ページ) の **[バックアップ メディアの既定の保有期間 (日)]** オプションで設定されています。 このオプションを表示するには、オブジェクト エクスプローラーでサーバー名を右クリックし、プロパティを選択してから **[データベースの設定]** ページを選択します。  
  
    -   バックアップ セットが特定の日付に期限切れになるようにするには、 **[日時指定]**をクリックし、セットの有効期限が切れる日付を入力します。  
  
         バックアップの有効期限の詳細については、「 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)」を参照してください。  
  
21. **[圧縮]** セクションで、 **[バックアップの圧縮の設定]** ドロップダウン リストを使用して適切な圧縮レベルを選択します。  [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] 以降では、 [バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)がサポートされています。 既定では、バックアップが圧縮されるかどうかは、 **backup-compression default** サーバー構成オプションの値によって決まります。 ただし、現在のサーバー レベルの既定の設定にかかわらず、 **[バックアップを圧縮する]**をオンにしてバックアップを圧縮することも、 **[バックアップを圧縮しない]**をオンにして圧縮しないようにすることもできます。  
  
     バックアップの圧縮の設定の詳細については、「 [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)」をご覧ください。  
  
22. **[暗号化]** セクションで、 **[バックアップを暗号化する]** チェック ボックスを使用して、バックアップを暗号化するかどうかを指定します。 **[アルゴリズム]** ドロップダウン リストを使用して、暗号化アルゴリズムを選択します。  **[証明書または非対称キー]** ドロップダウン リストを使用して、既存の証明書または非対称キーを選択します。 暗号化は SQL Server 2014 以降でサポートされます。 暗号化オプションの詳細については、「 [データベースのバックアップ &#40;バックアップ オプション ページ&#41;](../../relational-databases/backup-restore/back-up-database-backup-options-page.md)」を参照してください。  
  
  
[メンテナンス プラン ウィザード](../maintenance-plans/use-the-maintenance-plan-wizard.md) を使用して、データベースのバックアップを作成することができます。 

### <a name="examples"></a>使用例  
#### <a name="a--full-back-up-to-disk-to-default-location"></a>**A.**既定の場所のディスクへの完全バックアップ
この例では、 `Sales` データベースを既定のバックアップ場所にあるディスクにバックアップします。  `Sales` のバックアップはまだ作成されていません。
1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。

2.  **[データベース]**を展開して `Sales`を右クリックし、 **[タスク]**をポイントしてから **[バックアップ]**をクリックします。

3.  クリックして **OK**です。

#### <a name="b--full-back-up-to-disk-to-non-default-location"></a>**B.既定以外の場所のディスクへの完全バックアップ**
この例では、 `Sales` データベースを `E:\MSSQL\BAK`にあるディスクにバックアップします。  `Sales` のバックアップは既に作成されています。
1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。

2.  **[データベース]**を展開して `Sales`を右クリックし、 **[タスク]**をポイントしてから **[バックアップ]**をクリックします。

3.  **[全般]** ページの **[バックアップ先]** セクションで、 **[バックアップ先]** ドロップダウン リストから **[ディスク]** を選択します。

4.  **[削除]** をクリックして、既存のバックアップ ファイルをすべて削除します。

5.  **[追加]** をクリックすると、 **[バックアップ先の選択]** ダイアログ ボックスが開きます。

6.  `E:\MSSQL\BAK\Sales_20160801.bak` [ファイル名] **テキスト ボックスに「** 」と入力します。

7.  **[OK]**をクリックします。

8.  **[OK]**をクリックします。

#### <a name="c--create-an-encrypted-backup"></a>**C.暗号化されたバックアップの作成**
この例では、 `Sales` データベースを暗号化して既定のバックアップ場所にバックアップします。  [**データベース マスター キー**](../../relational-databases/security/encryption/create-a-database-master-key.md) は既に作成されています。  [**証明書**](../../t-sql/statements/create-certificate-transact-sql.md) は、 `MyCertificate`という名前で既に作成されています。 **データベース マスター キー** と **証明書** を作成する T-SQL の例については、「 [暗号化されたバックアップの作成](../../relational-databases/backup-restore/create-an-encrypted-backup.md)」をご覧ください。  
1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。

2.  **[データベース]**を展開して `Sales`を右クリックし、 **[タスク]**をポイントしてから **[バックアップ]**をクリックします。

3.  **[メディア オプション]** ページの **[メディアを上書きする]** セクションで、 **[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]**をオンにします。

4.  **[バックアップ オプション]** ページの **[暗号化]** セクションで、 **[バックアップを暗号化する]** チェック ボックスをオンにします。

5.  **[アルゴリズム]** ボックスの一覧から、 **[AES 256]**を選択します。

6.  **[証明書または非対称キー]** ボックスの一覧で、 `MyCertificate`を選択します。

7.  **[OK]**をクリックします。

#### <a name="d--back-up-to-the-azure-blob-storage-service"></a>**D.Azure BLOB ストレージ サービスへのバックアップ**
#### <a name="common-steps"></a>**一般的な手順**  
次の 3 つの例では、Microsoft Azure BLOB ストレージ サービスへの `Sales` のデータベースの完全バックアップを実行します。  ストレージ アカウント名は `mystorageaccount`です。  コンテナーは `myfirstcontainer`と呼ばれます。  簡潔にするため、最初の 4 つの手順をここに一度だけリストし、例はすべて **手順 5.**から始めます。
1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。

2.  **[データベース]**を展開して `Sales`を右クリックし、 **[タスク]**をポイントしてから **[バックアップ]**をクリックします。

3.  **[全般]** ページの **[宛先]** セクションで、 **[バックアップ先]** ドロップダウン リストから **[URL]** を選択します。

4.  **[追加]** をクリックすると、 **[バックアップ先の選択]** ダイアログ ボックスが開きます。

    **D1.URL へのストライプ バックアップで SQL Server 資格情報が既に存在する場合**  
保存されたアクセス ポリシーは読み取り、書き込み、および一覧表示権で作成されています。  SQL Server 資格情報 `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`は、保存されたアクセス ポリシーに関連付けられている Shared Access Signature を使用して作成されています。  
*
    5.  `https://mystorageaccount.blob.core.windows.net/myfirstcontainer` [Azure ストレージ コンテナー:] **テキスト ボックスから** を選択します。

    6.  **[バックアップ ファイル:]** テキスト ボックスに、「 `Sales_stripe1of2_20160601.bak`」と入力します。

    7.  **[OK]**をクリックします。

    8.  手順 **4.** と **5.**を繰り返します。

    9.  **[バックアップ ファイル:]** テキスト ボックスに、「 `Sales_stripe2of2_20160601.bak`」と入力します。

    10.  **[OK]**をクリックします。

    11.   **[OK]**をクリックします。

    **D2.Shared Access Signature は存在し、SQL Server 資格情報は存在しない場合**
  5.    `https://mystorageaccount.blob.core.windows.net/myfirstcontainer` [Azure ストレージ コンテナー:] **テキスト ボックスに「** 」と入力します。
  
  6.    **[共有アクセス ポリシー:]** テキスト ボックスに Shared Access Signature を入力します。
  
  7.    **[OK]**をクリックします。
  
  8.    **[OK]**をクリックします。

    **D3.Shared Access Signature が存在しない場合**
  5.    **[新しいコンテナー]** ボタンをクリックすると、 **[Microsoft サブスクリプションへの接続]** ダイアログ ボックスが開きます。  
  
  6.    **[Microsoft サブスクリプションへの接続]** ダイアログ ボックスに入力し、 **[OK]** をクリックして **[バックアップ先の選択]** ダイアログ ボックスに戻ります。  詳細については、「 [Microsoft Azure サブスクリプションへの接続](../../relational-databases/backup-restore/connect-to-a-microsoft-azure-subscription.md) 」を参照してください。
  
  7.    **[バックアップ先の選択]** ダイアログ ボックスで **[OK]** をクリックします。
  
  8.    **[OK]**をクリックします。

  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
### <a name="create-a-full-database-backup"></a>データベースの完全バックアップの作成  
  
1.  次の項目を指定した BACKUP DATABASE ステートメントを実行し、データベースの完全バックアップを作成します。  
  
    -   バックアップするデータベースの名前。  
  
    -   データベースの完全バックアップを書き込むバックアップ デバイス。  
  
     データベースの完全バックアップのための [!INCLUDE[tsql](../../includes/tsql-md.md)] の基本構文を次に示します。  
  
     BACKUP DATABASE *database*  
  
     TO *backup_device* [ **、**...*n* ]  
  
     [ WITH *with_options* [ **,**...*o* ] ] ;  
  
    |オプション|[説明]|  
    |------------|-----------------|  
    |*database*|バックアップするデータベースです。|  
    |*backup_device* [ **、**...*n* ]|バックアップ操作に使用する 1 ～ 64 個のバックアップ デバイスの一覧を指定します。 物理バックアップ デバイスを指定したり、対応する論理バックアップ デバイス (既に定義されている場合) を指定したりできます。 物理バックアップ デバイスを指定するには、DISK オプションまたは TAPE オプションを使用します。<br /><br /> { DISK &#124; TAPE } **=***physical_backup_device_name*<br /><br /> 詳細については、「[バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)」を参照してください。|  
    |WITH *with_options* [ **,**...*o* ]|必要に応じて、1 つ以上の追加オプション ( *o*) を指定します。 基本的な with オプションについては、手順 2. を参照してください。|  
  
2.  必要に応じて、1 つ以上の WITH オプションを指定します。 ここでは、一部の基本的な WITH オプションについて説明します。 すべての WITH オプションについては、「 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)」を参照してください。  
  
    -   基本的なバックアップ セット WITH オプション  
  
         { COMPRESSION | NO_COMPRESSION }  
         [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] 以降でのみ、このバックアップで [バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md) を実行するかどうかを指定し、サーバー レベルの既定値を上書きできます。  
  
         ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)  
         SQL Server 2014 以降でのみ、使用する暗号化アルゴリズムと暗号化の保護に使用する証明書または非対称キーを指定します。  
  
         DESCRIPTION **=** { **'***text***'** | **@***text_variable* }  
         バックアップ セットを記述したテキストを自由な形式で指定します。 文字列の長さは最大 255 文字です。  
  
         名前 **=** { *backup_set_name* | **@***backup_set_name_var* }  
         バックアップ セットの名前を指定します。 名前の長さは最大 128 文字です。 NAME を指定しないと、名前は空白になります。  
  
    -   基本的なバックアップ セット WITH オプション  
  
         既定では、BACKUP はバックアップを既存のメディア セットに追加し、既存のバックアップ セットを保持します。 これを明示的に指定するには、NOINIT オプションを使用します。 既存のバックアップ セットへの追加については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。  
  
         また、FORMAT オプションを使用して、バックアップ メディアをフォーマットすることもできます。  
  
         FORMAT [ **,** MEDIANAME**=** { *media_name* | **@***media_name_variable* } ] [ **,** MEDIADESCRIPTION **=** { *text* | **@***text_variable* } ]  
         FORMAT 句は、バックアップ メディアを初めて使用する場合や既存のデータをすべて上書きする場合に使用します。 必要に応じて、新しいメディアにメディア名と説明を割り当てます。  
  
        > [!IMPORTANT]  
        >  BACKUP ステートメントで FORMAT 句を使用すると、バックアップ メディアに格納されているバックアップが破棄されるので、十分注意して使用してください。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
  
#### <a name="a-back-up-to-a-disk-device"></a>**A.ディスク デバイスへのバックアップ**  
 次の例では、新しいメディア セットを作成する [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] を使用して、 `FORMAT` データベース全体をディスクにバックアップします。  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="b-back-up-to-a-tape-device"></a>**B.テープ デバイスへのバックアップ**  
 次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース全体をテープにバックアップし、以前のバックアップに追加します。  
  
```tsql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
#### <a name="c-back-up-to-a-logical-tape-device"></a>**C.論理テープ デバイスへのバックアップ**  
 次の例では、テープ ドライブ用の論理バックアップ デバイスを作成した後、 作成したデバイスに [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース全体をバックアップします。  
  
```tsql  
-- Create a logical backup device,   
-- AdventureWorks2012_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'AdventureWorks2012_Bak_Tape', '\\.\tape0'; USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
   TO AdventureWorks2012_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'AdventureWorks2012_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of AdventureWorks2012';  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
**Backup-SqlDatabase** コマンドレットを使用します。 データベースの完全バックアップであることを明示するには、 **-BackupAction**  パラメーターにその既定値 **Database**を指定します。 このパラメーターは、データベースの完全バックアップでは省略可能です。  

### <a name="examples"></a>使用例
#### <a name="a--full-local-backup"></a>**A.ローカルの完全バックアップ**  
次の例では、 `MyDB` データベースの完全なバックアップを、サーバー インスタンス `Computer\Instance`の既定のバックアップ場所に作成します。 オプションで、この例では **-BackupAction Database**を指定します。  
```powershell 
Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
```
 
#### <a name="b--full-backup-to-microsoft-azure"></a>**B.Microsoft Azure への完全バックアップ**  
次の例では、Microsoft Azure BLOB ストレージ サービスに `Sales` インスタンスのデータベース `MyServer` の完全バックアップを作成します。  保存されたアクセス ポリシーは読み取り、書き込み、および一覧表示権で作成されています。  SQL Server 資格情報 `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`は、保存されたアクセス ポリシーに関連付けられている Shared Access Signature を使用して作成されています。  PowerShell コマンドでは **BackupFile** パラメーターを使用して、場所 (URL) とバックアップ ファイル名を指定します。

```powershell  
import-module sqlps;
$container = 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer';
$FileName = 'Sales.bak';
$database = 'Sales';
$BackupFile = $container + '/' + $FileName ;
  
Backup-SqlDatabase -ServerInstance "MyServer" –Database $database -BackupFile $BackupFile;
```
 
 **SQL Server PowerShell プロバイダーを設定して使用するには**  
  
-   [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [データベースのバックアップ (SQL Server)](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [データベースの差分バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
-   [SSMS を使用したデータベース バックアップの復元](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [単純復旧モデルでのデータベース バックアップの復元 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)  
  
-   [完全復旧モデルで障害発生時点までデータベースを復元する方法 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restore-database-to-point-of-failure-full-recovery.md)  
  
-   [データベースを新しい場所に復元する &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
  
-   [メンテナンス プラン ウィザードの使用](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
## <a name="see-also"></a>参照  
**[SQL Server のバックアップと復元操作のトラブルシューティング](https://support.microsoft.com/en-us/kb/224071)**          
[バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)   
 [トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)   
 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [データベースのバックアップ &#40;全般ページ&#41;](../../relational-databases/backup-restore/back-up-database-general-page.md)   
 [データベースのバックアップ &#40;バックアップ オプション ページ&#41;](../../relational-databases/backup-restore/back-up-database-backup-options-page.md)   
 [差分バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)   
 [データベースの完全バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-database-backups-sql-server.md)  
  
  

