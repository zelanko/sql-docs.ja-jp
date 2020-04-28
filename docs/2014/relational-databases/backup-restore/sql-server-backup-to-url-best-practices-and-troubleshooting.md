---
title: SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ac34c95e7ee4dc6f57ef7d8806a7db1bb981a944
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "70175967"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>SQL Server Backup to URL に関するベスト プラクティスとトラブルシューティング
  このトピックでは、Azure Blob service との間の SQL Server のバックアップと復元に関するベスト プラクティスとトラブルシューティングのヒントを示します。  
  
 SQL Server のバックアップ操作または復元操作に Azure Blob Storage サービスを使用する方法の詳細については、次のトピックを参照してください。  
  
-   [Azure Blob Storage サービスを使った SQL Server のバックアップと復元](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [チュートリアル:Azure Blob Storage サービスへの SQL Server のバックアップと復元](../tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>バックアップの管理  
 バックアップを管理するための一般的な推奨事項を次に示します。  
  
-   BLOB を誤って上書きしないように、各バックアップに一意なファイル名を付けることをお勧めします。  
  
-   コンテナーを作成する際は、アクセス レベルを **private**に設定し、必要な認証情報を指定できるユーザーまたはアカウントだけがコンテナー内の BLOB の読み取りや書き込みを実行できるようにすることをお勧めします。  
  
-   Azure 仮想マシンで実行されている SQL Server のインスタンス上のデータベースの SQL Server については、リージョン間のデータ転送コストを回避するために、仮想マシンと同じリージョンのストレージアカウントを使用します。 また、同じ地域を使用すると、バックアップ操作と復元操作で最適なパフォーマンスを得ることができます。  
  
-   バックアップ処理に失敗すると、無効なバックアップ ファイルが生成されます。 失敗したバックアップを定期的に確認し、BLOB ファイルを削除することをお勧めします。 詳細については、「 [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)」をご覧ください。  
  
-   バックアップ中に `WITH COMPRESSION` オプションを使用すると、ストレージ コストとストレージのトランザクション コストを最小限に抑えることができます。 また、バックアップ プロセスが完了するまでにかかる時間を短縮することもできます。  
  
## <a name="handling-large-files"></a>大きなファイルの処理  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバックアップ操作では、複数のスレッドを使用して、Azure Blob Storage サービスへのデータ転送が最適化されます。  ただし、パフォーマンスは ISV の帯域幅やデータベースのサイズなどのさまざまな要因によって異なります。 内部設置型の SQL Server データベースから大きなデータベースまたはファイル グループをバックアップする場合は、最初にスループットのテストを行うことをお勧めします。 [Azure storage の SLA](https://go.microsoft.com/fwlink/?LinkId=271619)には、考慮する必要がある blob の最大処理時間があります。  
  
-   「**バックアップの管理**」セクションで推奨されているように `WITH COMPRESSION` オプションを使用することは、大きなファイルをバックアップするときに非常に重要です。  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>BACKUP TO URL または RESTORE FROM URL のトラブルシューティング  
 ここでは、Azure Blob Storage サービスへのバックアップまたは Azure Blob Storage サービスからの復元を実行するときに発生するエラーを簡単にトラブルシューティングする方法をいくつか示します。  
  
 サポートされていないオプションまたは制限事項によるエラーを回避するには、「 [Azure Blob Storage サービスを使用したバックアップと復元 SQL Server](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) 」の記事に記載されている制限事項の一覧および backup コマンドと restore コマンドのサポートに関する情報を参照してください。  
  
 **認証エラー:**  
  
-   WITH CREDENTIAL は新しいオプションで、Azure Blob ストレージサービスとの間でバックアップまたは復元を行うために必要です。 資格情報に関連するエラーには、次のようなものがあります。  
  
     `BACKUP` コマンドまたは `RESTORE` コマンドで指定された資格情報が存在しません。 この問題を回避するには、資格情報が BACKUP ステートメントに存在しない場合に資格情報を作成する T-SQL ステートメントを含めることができます。 使用可能な例を次に示します。  
  
    ```  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
  
    ```  
  
-   資格情報は存在しますが、BACKUP コマンドの実行に使用されるログイン アカウントに資格情報へのアクセス権限がありません。 **Alter any credential** 権限がある **db_backupoperator** ロールのログイン アカウントを使用してください。  
  
-   ストレージ アカウントの名前とキーの値を確認してください。 資格情報に格納されている情報は、バックアップ操作と復元操作で使用する Azure ストレージ アカウントのプロパティの値と一致する必要があります。  
  
 **バックアップ エラー/障害:**  
  
-   同じ BLOB への並列バックアップを実行すると、バックアップの 1 つが " **初期化に失敗しました** " エラーで失敗します。  
  
-   次のエラー ログを使用して、バックアップ エラーのトラブルシューティングに役立ててください。  
  
    -   トレース フラグ 3051 を設定して、次の形式の特定のエラー ログへの記録を有効にします。  
  
         BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log。ここで、\<action> には次のいずれかを指定します。  
  
        -   `DB`  
  
        -   `FILELISTONLY`  
  
        -   `LABELONLY`  
  
        -   `HEADERONLY`  
  
        -   `VERIFYONLY`  
  
    -   "SQLBackupToUrl" という名前の [アプリケーションログ] の下にある Windows イベントログを確認して、情報を検索することもできます。  
  
-   圧縮されたバックアップから復元するときに、次のエラーが表示される場合があります。  
  
    -   **SqlException 3284 が発生しました。重大度:16、状態: 5**  
        **デバイス 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' のメッセージマークは、アラインされていません。Backupset の作成に使用したのと同じブロックサイズを使用して Restore ステートメントを再実行してください: ' 65536 ' は、可能な値のように見えます。**  
  
         このエラーを解決するには、`BACKUP` を指定した `BLOCKSIZE = 65536` ステートメントを再実行してください。  
  
-   アクティブなリースを保持している BLOB が原因でバックアップ中に発生するエラー: バックアップ処理に失敗すると、アクティブなリースを保持する BLOB が生成されます。  
  
     BACKUP ステートメントが再実行されると、バックアップ操作が次のようなエラーで失敗することがあります。  
  
     **Backup to URL はリモート エンドポイントから例外を受け取りました。例外メッセージ: リモート サーバーからエラーが返されました: (412) 現在 BLOB にリースがありますが、要求にリース ID が指定されていません**。  
  
     アクティブなリースを保持しているバックアップ BLOB ファイルに対して RESTORE ステートメントが実行されると、復元操作は次のようなエラーで失敗します。  
  
     **例外メッセージ: リモート サーバーからエラーが返されました: (409) 競合。**  
  
     このようなエラーが発生した場合は、BLOB ファイルを削除する必要があります。 このシナリオの詳細とこの問題の解決方法については、「 [Deleting Backup Blob Files with Active Leases](deleting-backup-blob-files-with-active-leases.md)」を参照してください。  
  
## <a name="proxy-errors"></a>プロキシ エラー  
 インターネットへのアクセスにプロキシ サーバーを使用している場合、以下の問題が発生することがあります。  
  
 **プロキシ サーバーによる接続数の設定:**  
  
 プロキシ サーバーで、1 分あたりの接続数を制限する設定が使用されている場合があります。 Backup to URL プロセスはマルチスレッド プロセスであるため、この制限を超える可能性があります。 制限を超えた場合、プロキシ サーバーは接続を切断します。 この問題を解決するには、プロキシ設定を変更し、SQL Server がプロキシを使用しないようにします。   エラー ログに表示される可能性のある種類またはエラー メッセージの例を次に示します。  
  
-   "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" への書き込みに失敗しました: BACKUP to URL がリモートエンドポイントから例外を受け取りました。 例外メッセージ: 転送接続からデータを読み取ることができません: 接続は閉じられました。  
  
-   ファイル "http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" で回復できない I/O エラーが発生しました。リモート エンドポイントからエラーを収集できませんでした。  
  
     メッセージ 3013、レベル 16、状態 1、行 2  
  
     バックアップ データベースが異常終了しています。  
  
-   BackupIoRequest:: ReportIoError: バックアップデバイス 'http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak' で書き込みエラーが発生しています。 Backup to URL がリモート エンドポイントから例外を受け取ったオペレーティング システム エラーです。 例外メッセージ: 転送接続からデータを読み取ることができません: 接続は閉じられました。  
  
 トレース フラグ 3051 を使用して詳細ログを有効にすると、ログに次のメッセージが表示される場合もあります。  
  
 HTTP ステータス コード 502、HTTP ステータス メッセージ プロキシ エラー (1 分あたりの HTTP 要求数が構成済みの上限を超えました。 ISA Server 管理者に連絡してください。)  )  
  
 **選択されていない既定のプロキシ設定:**  
  
 既定の設定が選択されていないことが原因で、次に示すようなプロキシ認証エラーが発生することがあります。 "*http://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" というファイルで回復不可能な i/o エラーが発生しました。 Backup to URL がリモートエンドポイントから例外を受け取りました。例外メッセージ: リモートサーバーからエラーが返されました: (407)* **プロキシ認証が必要**です。  
  
 この問題を解決するには、次の手順に従って、Backup to URL プロセスで既定のプロキシ設定を使用できるようにするための構成ファイルを作成します。  
  
1.  次の xml を使用して、BackuptoURL.exe.config という名前の構成ファイルを作成します。  
  
    ```  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
  
    ```  
  
2.  SQL Server インスタンスの Binn フォルダーに構成ファイルを配置します。 たとえば、SQL Server がコンピューターの C ドライブにインストールされている場合は、構成ファイルを*C:\Program SERVER\MSSQL12.\< SQL に配置します。InstanceName> \MSSQL\Binn*。  
  
## <a name="troubleshooting-sql-server-managed-backup-to-azure"></a>Azure への管理されたバックアップ SQL Server のトラブルシューティング  
 SQL Server マネージド バックアップは Backup to URL の上に構築されるので、前のセクションで説明したトラブルシューティングのヒントは、SQL Server マネージド バックアップを使用するデータベースまたはインスタンスに適用されます。  Azure への管理されたバックアップ SQL Server のトラブルシューティングの詳細については、「 [azure へのマネージバックアップのトラブルシューティング SQL Server](sql-server-managed-backup-to-microsoft-azure.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Azure に格納されたバックアップからの復元](restoring-from-backups-stored-in-microsoft-azure.md)  
  
  
