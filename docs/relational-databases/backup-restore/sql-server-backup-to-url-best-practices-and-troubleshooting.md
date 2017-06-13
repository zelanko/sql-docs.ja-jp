---
title: "SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング | Microsoft Docs"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: c0e55c0e35039490f0ce4cd8a7fb6d7e232c05aa
ms.openlocfilehash: b76a0f262fd12e53797c0ad86c991a6e4423927a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/15/2017

---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックには、Windows Azure BLOB サービスとの間の SQL Server のバックアップと復元に関するベスト プラクティスとトラブルシューティングのヒントを示しています。  
  
 SQL Server のバックアップ操作または復元操作に Windows Azure BLOB スレージ サービスを使用する方法の詳細については、次のトピックを参照してください。  
  
-   [Microsoft Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [チュートリアル: Windows Azure BLOB ストレージ サービスへの SQL Server のバックアップと復元](~/relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>バックアップの管理  
 バックアップを管理するための一般的な推奨事項を次に示します。  
  
-   BLOB を誤って上書きしないように、各バックアップに一意なファイル名を付けることをお勧めします。  
  
-   コンテナーを作成する際は、アクセス レベルを **private**に設定し、必要な認証情報を指定できるユーザーまたはアカウントだけがコンテナー内の BLOB の読み取りや書き込みを実行できるようにすることをお勧めします。  
  
-   Windows Azure バーチャル マシンで実行している SQL Server インスタンス上の SQL Server データベースでは、バーチャル マシンと同じ地域のストレージ アカウントを使用して、地域間のデータ転送コストを回避してください。 また、同じ地域を使用すると、バックアップ操作と復元操作で最適なパフォーマンスを得ることができます。  
  
-   バックアップ処理に失敗すると、無効なバックアップ ファイルが生成されます。 失敗したバックアップを定期的に確認し、BLOB ファイルを削除することをお勧めします。 詳細については、「 [Deleting Backup Blob Files with Active Leases](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)」をご覧ください。  
  
-   バックアップ中に **WITH COMPRESSION** オプションを使用すると、ストレージ コストとストレージのトランザクション コストを最小限に抑えることができます。 また、バックアップ プロセスが完了するまでにかかる時間を短縮することもできます。  
  
## <a name="handling-large-files"></a>大きなファイルの処理  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップ操作では、複数のスレッドを使用して、Windows Azure BLOB ストレージ サービスへのデータ転送を最適化します。  ただし、パフォーマンスは ISV の帯域幅やデータベースのサイズなどのさまざまな要因によって異なります。 内部設置型の SQL Server データベースから大きなデータベースまたはファイル グループをバックアップする場合は、最初にスループットのテストを行うことをお勧めします。 [SLA for Storage](http://azure.microsoft.com/support/legal/sla/storage/v1_0/) には BLOB の最大処理時間が示されているため、考慮に入れておくことができます。  
  
-   「 **バックアップの管理** 」セクションで推奨している方法で **WITH COMPRESSION** オプションを使用することは、大きなファイルをバックアップするときに非常に重要です。  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>BACKUP TO URL または RESTORE FROM URL のトラブルシューティング  
 ここでは、Windows Azure BLOB ストレージ サービスへのバックアップまたは Windows Azure BLOB ストレージ サービスからの復元を実行する際に発生するエラーを簡単にトラブルシューティングする方法をいくつか示します。  
  
 サポートされないオプションまたは制限事項によるエラーを回避するには、「 [Microsoft Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) 」の記事で、制限事項の一覧および BACKUP コマンドと RESTORE コマンドのサポート情報を確認してください。  
  
 **認証エラー:**  
  
-   WITH CREDENTIAL は新しいオプションで、Windows Azure BLOB ストレージ サービスへのバックアップまたは Windows Azure BLOB ストレージ サービスからの復元に必要です。 資格情報に関連するエラーには、次のようなものがあります。  
  
     **BACKUP** コマンドまたは **RESTORE** コマンドで指定された資格情報が存在しません。 この問題を回避するには、資格情報が BACKUP ステートメントに存在しない場合に資格情報を作成する T-SQL ステートメントを含めることができます。 使用可能な例を次に示します。  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   資格情報は存在しますが、BACKUP コマンドの実行に使用されるログイン アカウントに資格情報へのアクセス権限がありません。 **Alter any credential** 権限がある **db_backupoperator** ロールのログイン アカウントを使用してください。  
  
-   ストレージ アカウントの名前とキーの値を確認してください。 資格情報に格納されている情報は、バックアップ操作と復元操作で使用する Windows Azure ストレージ アカウントのプロパティ値と一致する必要があります。  
  
 **バックアップ エラー/障害:**  
  
-   同じ BLOB への並列バックアップを実行すると、バックアップの 1 つが " **初期化に失敗しました** " エラーで失敗します。  
  
-   次のエラー ログを使用して、バックアップ エラーのトラブルシューティングに役立ててください。  
  
    -   トレース フラグ 3051 を設定して、次の形式の特定のエラー ログへの記録を有効にします。  
  
         BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log。ここで、\<action> には次のいずれかを指定します。  
  
        -   **DB (DB)**  
  
        -   **FILELISTONLY**  
  
        -   **LABELONLY**  
  
        -   **HEADERONLY**  
  
        -   **VERIFYONLY**  
  
    -   Windows イベント ログ ('SQLBackupToUrl' という名前のアプリケーション ログ) を確認することで情報を見つけることもできます。  
  
-   圧縮されたバックアップから復元するときに、次のエラーが表示される場合があります。  
  
    -   `SqlException 3284 occurred. Severity: 16 State: 5`  
        **デバイス`'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak'`が無効です。バックアップセットの作成に使用したのと同じブロック サイズを指定して RESTORE ステートメントを再実行してください。使用した可能性のある値は '65536' です。**  
  
         このエラーを解決するには、 **BLOCKSIZE = 65536** を指定した **BACKUP** ステートメントを再実行してください。  
  
-   アクティブなリースを保持している BLOB が原因でバックアップ中に発生するエラー: バックアップ処理に失敗すると、アクティブなリースを保持する BLOB が生成されます。  
  
     BACKUP ステートメントが再実行されると、バックアップ操作が次のようなエラーで失敗することがあります。  
  
     **Backup to URL はリモート エンドポイントから例外を受け取りました。例外メッセージ: リモート サーバーからエラーが返されました: (412) 現在 BLOB にリースがありますが、要求にリース ID が指定されていません**。  
  
     アクティブなリースを保持しているバックアップ BLOB ファイルに対して RESTORE ステートメントが実行されると、復元操作は次のようなエラーで失敗します。  
  
     **例外メッセージ: リモート サーバーからエラーが返されました: (409) 競合。**  
  
     このようなエラーが発生した場合は、BLOB ファイルを削除する必要があります。 このシナリオの詳細とこの問題の解決方法については、「 [Deleting Backup Blob Files with Active Leases](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)」を参照してください。  
  
## <a name="proxy-errors"></a>プロキシ エラー  
 インターネットへのアクセスにプロキシ サーバーを使用している場合、以下の問題が発生することがあります。  
  
 **プロキシ サーバーによる接続数の設定:**  
  
 プロキシ サーバーで、1 分あたりの接続数を制限する設定が使用されている場合があります。 Backup to URL プロセスはマルチスレッド プロセスであるため、この制限を超える可能性があります。 制限を超えた場合、プロキシ サーバーは接続を切断します。 この問題を解決するには、プロキシ設定を変更し、SQL Server がプロキシを使用しないようにします。   エラー ログに表示される可能性のある種類またはエラー メッセージの例を次に示します。  
  
-   "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" での書き込みに失敗しました: Backup to URL がリモート エンドポイントから例外を受け取りました。 例外メッセージ: 転送接続からデータを読み取ることができません: 接続は閉じられました。  
  
-   ファイルで回復不可能な I/O エラーが発生しました"`http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:`"リモート エンドポイントからエラーを収集できませんでした。  
  
     メッセージ 3013、レベル 16、状態 1、行 2  
  
     バックアップ データベースが異常終了しています。  
  
-   BackupIoRequest::ReportIoError: バックアップ デバイス http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak。 Backup to URL がリモート エンドポイントから例外を受け取ったオペレーティング システム エラーです。 例外メッセージ: 転送接続からデータを読み取ることができません: 接続は閉じられました。  
  
 トレース フラグ 3051 を使用して詳細ログを有効にすると、ログに次のメッセージが表示される場合もあります。  
  
 HTTP ステータス コード 502、HTTP ステータス メッセージ プロキシ エラー (1 分あたりの HTTP 要求数が構成済みの上限を超えました。 ISA Server 管理者に連絡してください。)  )  
  
 **選択されていない既定のプロキシ設定:**  
  
 場合によって、既定の設定が選択されていない原因プロキシ認証エラーなど、次のように:*ファイルで回復不可能な I/O エラーが発生しました"`http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:`"Backup to URL がリモート エンドポイントから例外を受け取りました。例外メッセージ: リモート サーバーからエラーが返されました: (407)* **プロキシ認証が必要です**。  
  
 この問題を解決するには、次の手順に従って、Backup to URL プロセスで既定のプロキシ設定を使用できるようにするための構成ファイルを作成します。  
  
1.  次の xml を使用して、BackuptoURL.exe.config という名前の構成ファイルを作成します。  
  
    ```  
    \<?xml version ="1.0"?>  
    <configuration>   
                    \<system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    \</system.net>  
    </configuration>  
  
    ```  
  
2.  SQL Server インスタンスの Binn フォルダーに構成ファイルを配置します。 たとえば、SQL Server がコンピューターの C ドライブにインストールされている場合は、構成ファイルを *C:\Program Files\Microsoft SQL Server\MSSQL13.\<InstanceName>\MSSQL\Binn* に配置します。  
  
## <a name="see-also"></a>参照  
 [Microsoft Azure に格納されたバックアップからの復元](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)
  

