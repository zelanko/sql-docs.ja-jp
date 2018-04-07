---
title: 並列データ ウェアハウスの transparent Data Encryption
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: 透過的なデータ暗号化 (TDE) は、データとトランザクション ログ ファイルと、特別な PDW ログ ファイルのリアルタイムの I/O の暗号化と解読を実行します。
ms.date: 10/20/2016
ms.topic: article
ms.assetid: b82ad21d-09dd-43dd-8fab-bcf2c8c3ac6d
caps.latest.revision: 22
ms.openlocfilehash: d93d76018baeed1577b6831cbde359002c89416e
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="transparent-data-encryption"></a>透過的なデータ暗号化
データベースをセキュリティで保護するために、安全なシステムの設計、機密資産の暗号化、データベース サーバーに対するファイアウォールの構築などの予防策を講じることができます。 ただし、物理メディア (ドライブやバックアップ テープなど) が盗まれた場合は、悪意のある人物によってデータベースが復元またはアタッチされ、データが参照されるおそれがあります。 解決策の 1 つは、データベース内の機密データを暗号化し、データの暗号化に使用されるキーを証明書で保護することです。 これにより、キーを持たない人物によるデータの使用を防止できますが、このような保護は事前に計画する必要があります。  
  
*透過的なデータ暗号化*(TDE) は、データのリアルタイムの I/O の暗号化と解読を実行し、トランザクション ログ ファイルと特殊な PDW ログ ファイルです。 暗号化にはデータベース暗号化キー (DEK) が使用されます。これは、復旧時に使用できるようにデータベース ブート レコードに保存されます。 DEK は、SQL Server PDW の master データベースに格納されている証明書を使用して、セキュリティで保護された対称キーです。 TDE では、"静止した" データ、つまりデータとログ ファイルが保護されます。 この暗号化は、法律、規制、およびさまざまな業界で確立されているガイドラインの多くに準拠できるようになっています。 これによりソフトウェア開発者は、既存のアプリケーションを変更することなく、AES および 3DES 暗号化アルゴリズムを使用してデータを暗号化できます。  
  
> [!IMPORTANT]  
> TDE では、クライアントと PDW 間を移動するデータの暗号化は提供されません。 クライアントと SQL Server PDW の間でデータを暗号化する方法の詳細については、次を参照してください。[証明書をプロビジョニング](provision-certificate.md)です。  
>   
> TDE では、移動中、または使用中で、データは暗号化されません。 SQL Server PDW 内の PDW コンポーネント間の内部のトラフィックは暗号化されません。 メモリ バッファーに一時的に格納されたデータは暗号化されません。 このリスクを軽減するのには、物理的なアクセスおよび SQL Server PDW への接続を制御します。  
  
セキュリティで保護されたデータベースは、正しい証明書を使用することで復元できます。  
  
> [!NOTE]  
> TDE の証明書を作成するときにする必要があります直ちにバックアップすること、関連付けられた秘密キーと共にします。 証明書が使用できなくなった場合、またはデータベースを別のサーバーに復元またはアタッチする必要がある場合に、証明書と秘密キーの両方のバックアップが必要です。これらのバックアップがない場合は、データベースを開けません。 暗号化証明書は、データベースで TDE を無効にした場合でも保持する必要があります。 データベースが暗号化されていない場合でも、トランザクション ログの一部はまだ保護されたままである場合があるため、データベースの完全バックアップが実行されるまでは、一部の操作では証明書が必要な場合があります。 有効期限の日付を過ぎた証明書であっても、TDE によりデータを暗号化および暗号化解除できる場合があります。  
  
データベース ファイルの暗号化は、ページ レベルで実行されます。 暗号化されたデータベースのページは、ディスクに書き込まれる前に暗号化され、メモリに読み込まれるときに暗号化解除されます。 TDE では、暗号化されたデータベースのサイズが増えることはありません。  
  
次の図は、TDE 暗号化のキーの階層を示しています。  
  
![トピックで説明された階層を表示します。] (media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-tde"></a>Transparent Data Encryption の使用  
TDE を使用するには、次の手順を実行します。 最初の 3 つの手順は一度だけ実行 TDE をサポートする SQL Server PDW の準備をする場合。  
  
1.  Master データベースのマスター _ キーを作成します。  
  
2.  使用して**sp_pdw_database_encryption**を SQL Server PDW で TDE を有効にします。 この操作は、将来の一時データの保護を実現するために、一時的なデータベースを変更し、一時テーブルを持つアクティブなセッションがある場合にしようとした場合は失敗します。 **sp_pdw_database_encryption**ユーザー データのマスキング PDW システム ログをオンにします。 (ユーザー データのマスキング PDW システム ログの詳細については、次を参照してください[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)。)。  
  
3.  使用して[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)認証および証明書のバックアップが格納される共有への書き込みできる資格情報を作成します。 目的の記憶域サーバーの資格情報が既に存在する場合は、既存の資格情報を使用できます。  
  
4.  Master データベースでは、マスター _ キーによって保護される証明書を作成します。  
  
5.  記憶域共有に証明書をバックアップします。  
  
6.  ユーザー データベースでデータベース暗号化キーを作成し、master データベースに格納されている証明書で保護します。  
  
7.  使用して、 `ALTER DATABASE` TDE を使用してデータベースを暗号化するステートメント。  
  
次の例は、暗号化を示しています、`AdventureWorksPDW2012`という証明書を使用してデータベース`MyServerCert`SQL Server PDW で作成された。  
  
**1: SQL Server PDW で TDE を有効にします。** これはのみに必要な 1 回です。  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
-- Add a credential that can write to the share  
-- A credential created for a backup can be used if you wish  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
**: 2 番目のコード例を作成して、master データベース内の証明書をバックアップします。** これは 1 回が必要です。 (推奨)、データベースごとに別の証明書をも、1 つの証明書に複数のデータベースを保護することができます。  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert WITH SUBJECT = 'My DEK Certificate';  
GO  
  
-- Back up the certificate with private key  
BACKUP CERTIFICATE MyServerCert   
    TO FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'  
    WITH PRIVATE KEY   
    (   
        FILE = '\\SECURE_SERVER\cert\MyServerCert.key',  
        ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>'   
    )   
GO  
```  
  
**: 最後は、DEK を作成し、ユーザー データベースの暗号化に ALTER DATABASE を使用します。** これは、TDE で保護されているデータベースごとに繰り返されます。  
  
```sql  
USE AdventureWorksPDW2012;  
GO  
  
CREATE DATABASE ENCRYPTION KEY  
WITH ALGORITHM = AES_128  
ENCRYPTION BY SERVER CERTIFICATE MyServerCert;  
GO  
  
ALTER DATABASE AdventureWorksPDW2012 SET ENCRYPTION ON;  
GO  
```  
  
暗号化および暗号化解除の操作は、SQL Server によってバック グラウンド スレッドでスケジュールされます。 これらの操作の状態は、この後の一覧に示すカタログ ビューおよび動的管理ビューを使用して確認できます。  
  
> [!CAUTION]  
> TDE が有効になっているデータベースのバックアップ ファイルも、データベース暗号化キーを使用して暗号化されます。 このため、このバックアップを復元するときには、データベース暗号化キーを保護している証明書が必要です。 つまり、データの損失を防ぐには、データベースをバックアップするだけでなく、サーバー証明書のバックアップも確実に保守する必要があります。 証明書が使用できなくなると、データの損失が発生します。  
  
## <a name="commands-and-functions"></a>コマンドと関数  
TDE の証明書を次に示すステートメントで処理できるようにするには、この証明書をデータベース マスター キーで暗号化する必要があります。  
  
次の表に、TDE のコマンドと関数の説明とリンクを示します。  
  
|コマンドまたは関数|用途|  
|-----------------------|-----------|  
|[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)|データベースの暗号化に使用されるキーを作成します。|  
|[ALTER DATABASE ENCRYPTION KEY](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|データベースの暗号化に使用されるキーを変更します。|  
|[DROP DATABASE ENCRYPTION KEY](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|データベースの暗号化に使用されたキーを削除します。|  
|[ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md)|TDE を有効にするために使用される **ALTER DATABASE** オプションについて説明します。|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>カタログ ビューと動的管理ビュー  
次の表に、TDE のカタログ ビューと動的管理ビューを示します。  
  
|カタログ ビューまたは動的管理ビュー|用途|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|データベース情報を表示するカタログ ビュー|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|データベース内の証明書を表示するカタログ ビュー|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|各ノードのデータベース、およびデータベースの暗号化の状態で使用される暗号化キーに関する情報を提供する動的管理ビュー。|  
  
## <a name="permissions"></a>権限  
TDE の各機能とコマンドには、上の表で説明されているように、個別の権限要件があります。  
  
TDE に関係するメタデータを表示する必要があります、`CONTROL SERVER`権限です。  
  
## <a name="considerations"></a>考慮事項  
データベース暗号化操作の再暗号化スキャンが実行されている間は、データベースに対するメンテナンス操作が無効になります。  
  
使用してデータベース暗号化の状態を調べることができます、 **sys.dm_pdw_nodes_database_encryption_keys**動的管理ビュー。 詳細については、次を参照してください。、*カタログ ビューおよび動的管理ビュー*このトピックの前半の「)。  
  
### <a name="restrictions"></a>制限  
中に、次の操作は許可されていません、 `CREATE DATABASE ENCRYPTION KEY`、 `ALTER DATABASE ENCRYPTION KEY`、 `DROP DATABASE ENCRYPTION KEY`、または`ALTER DATABASE...SET ENCRYPTION`ステートメントです。  
  
-   データベースの削除。  
  
-   使用して、`ALTER DATABASE`コマンド。  
  
-   データベースのバックアップを開始しています。  
  
-   データベースの復元を開始しています。  
  
次の操作または状況が回避されます、 `CREATE DATABASE ENCRYPTION KEY`、 `ALTER DATABASE ENCRYPTION KEY`、 `DROP DATABASE ENCRYPTION KEY`、または`ALTER DATABASE...SET ENCRYPTION`ステートメントです。  
  
-   `ALTER DATABASE`コマンドを実行します。  
  
-   データ バックアップが実行されている。  
  
データベース ファイルを作成する際には、TDE が有効になっているとファイルの瞬時初期化を使用できません。  
  
### <a name="areas-not-protected-by-tde"></a>TDE で保護されていない領域  
TDE では、外部テーブルは保護されません。  
  
TDE では、診断セッションを保護しません。 ユーザーが注意する必要が診断セッションが使用中に機密性の高いパラメーターを持つクエリにありません。 不要になったとすぐに、機密情報を表示する診断セッションを削除する必要があります。  
  
SQL Server PDW のメモリに配置されたときに、TDE で保護されたデータが暗号化解除されます。 メモリ ダンプは、アプライアンスの特定の問題が発生したときに作成されます。 ダンプ ファイルを示すコンテンツ メモリの問題の外観の時に、暗号化されていない形式で機密データを含めることができます。 他のユーザーと共有する前に、メモリ ダンプの内容を確認する必要があります。  
  
Master データベースが TDE で保護されていません。 Master データベースにユーザー データが含まれていない、ログイン名などの情報は含まれて。  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Transparent Data Encryption とトランザクション ログ  
TDE に使用するデータベースを有効にすると、強制的に次の仮想トランザクション ログに、仮想トランザクション ログの残りの部分の領域の解放の効果があります。 これにより、データベースが暗号化対象として設定された後にトランザクション ログにクリア テキストが残らないことが保証されます。 PDW の各ノードで表示して、ログ ファイルの暗号化の状態を確認する、`encryption_state`内の列、`sys.dm_pdw_nodes_database_encryption_keys`例のように、ビュー。  
  
```sql  
WITH dek_encryption_state AS   
(  
    SELECT ISNULL(db_map.database_id, dek.database_id) AS database_id, encryption_state  
    FROM sys.dm_pdw_nodes_database_encryption_keys AS dek  
        INNER JOIN sys.pdw_nodes_pdw_physical_databases AS node_db_map  
           ON dek.database_id = node_db_map.database_id AND dek.pdw_node_id = node_db_map.pdw_node_id  
        LEFT JOIN sys.pdw_database_mappings AS db_map  
            ON node_db_map .physical_name = db_map.physical_name  
        INNER JOIN sys.dm_pdw_nodes AS nodes  
            ON nodes.pdw_node_id = dek.pdw_node_id  
    WHERE dek.encryptor_thumbprint <> 0x  
)  
SELECT TOP 1 encryption_state  
       FROM dek_encryption_state  
       WHERE dek_encryption_state.database_id = DB_ID('AdventureWorksPDW2012 ')  
       ORDER BY (CASE encryption_state WHEN 3 THEN -1 ELSE encryption_state END) DESC;  
```  
  
データベース暗号化キーを変更する前にトランザクション ログに書き込まれたデータは、以前のデータベース暗号化キーで暗号化されます。  
  
### <a name="pdw-activity-logs"></a>PDW のアクティビティ ログ  
SQL Server PDW では、一連のトラブルシューティングのログを保持します。 なお、これは、トランザクション ログ、SQL Server エラー ログまたは Windows イベント ログ。これらの PDW アクティビティ ログは、一部のユーザー データを含めることができます、クリア テキストで、完全なステートメントを含めることができます。 典型的な例は**挿入**と**更新**ステートメントです。 ユーザー データのマスキングできますで明示的に有効または無効を使用して**sp_pdw_log_user_data_masking**です。 保護するために PDW 動作状況のログ内のユーザー データのマスキングを有効に自動的に SQL Server PDW の暗号化を有効にします。 **sp_pdw_log_user_data_masking** TDE を使用していないときにステートメントをマスクするも使用できますが、Microsoft サポート チームが問題を分析する機能が大幅に減るために推奨されていません。  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Transparent Data Encryption と tempdb システム データベース  
使用して暗号化が有効になっているときに、tempdb システム データベースは暗号化は[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)です。 これは、機能は、任意のデータベースが TDE を使用する前に必要です。 これには、SQL Server PDW の同じインスタンスで暗号化されていないデータベースのパフォーマンスに影響があります。  
  
## <a name="key-management"></a>キー管理  
データベース暗号化キー (DEK) は、master データベースに格納されている証明書によって保護されます。 これらの証明書は、master データベースのデータベース マスター_キー (DMK) によって保護されます。 DMK は、TDE に使用するために、サービス マスター _ キー (SMK) で保護する必要があります。  
  
システムは、(パスワードの入力) などの人間の介入を必要とせず、キーにアクセスできます。 証明書が使用できない場合、システムは、適切な証明書が利用可能になるまで、DEK を解読できないことを示すエラー メッセージを出力します。  
  
証明書が使用を保護する 1 つのアプライアンスから別のデータベースを移動する場合、' DEK は、移行先サーバーで最初復元する必要があります。 通常どおり、データベースを復元できます。 詳細についてで標準の SQL Server のマニュアルを参照してください。 [TDE で保護されているデータベースを別の SQL Server に移動](http://technet.microsoft.com/library/ff773063.aspx)です。  
  
それらを使用するデータベース バックアップが実行されている限り、Dek の暗号化に使用される証明書を保持する必要があります。 証明書のバックアップは、データベースの復元の秘密キーのない証明書を使用できないために、証明書の秘密キーを含める必要があります。 これらの証明書の秘密キー バックアップは、証明書の復元を指定する必要がありますをパスワードで保護されている別のファイルに格納されます。  
  
## <a name="restoring-the-master-database"></a>Master データベースの復元  
使用して、master データベースを復元できます**DWConfig**、障害回復の一部として。  
  
-   コントロールのノードが変更されていない場合ですが、master データベースが復元した場合、変更されていないと同じアプライアンスに master データベースのバックアップの取得元となる、DMK とすべての証明書になりますアクションを追加せずに読み取り可能です。  
  
-   Master データベースは、異なるアプライアンスで復元する場合、またはコントロールのノードは、master データベースのバックアップ以降に変更されている場合は、追加の手順を DMK を再生成するために必要があります。  
  
    1.  DMK を開きます。  
  
        ```sql  
        OPEN MASTER KEY DECRYPTION BY PASSWORD = '<password>';  
        ```  
  
    2.  SMK による暗号化を追加します。  
  
        ```sql  
        ALTER MASTER KEY   
            ADD ENCRYPTION BY SERVICE MASTER KEY;  
        ```  
  
    3.  アプライアンスを再起動します。  
  
## <a name="upgrade-and-replacing-virtual-machines"></a>アップグレードと仮想マシンの交換  
アップグレードまたは置換 VM が実行されたアプライアンス上、DMK が存在する場合は、パラメーターとして DMK パスワードを指定する必要があります。  
  
アップグレード アクションの例です。 置き換える`**********`DMK パスワードを使用します。  
  
`setup.exe /Action=ProvisionUpgrade … DMKPassword='**********'  `  
  
[置換] バーチャル マシン操作の例です。  
  
`setup.exe /Action=ReplaceVM … DMKPassword='**********'  `  
  
アップグレード中に、ユーザー データベースが暗号化され、DMK パスワードが指定されていない、アップグレード操作は失敗します。 置換、中に、DMK が存在する場合、正しいパスワードが指定されていない操作がその DMK 復旧ステップをスキップします。 その他のすべての手順は追加の手順が必要なことを示すために、最後のエラーを報告するアクションが [置換] VM 操作の最後に完了できません。 セットアップ ログで (内にある**\ProgramData\Microsoft\Microsoft SQL Server Parallel Data Warehouse\100\Logs\Setup\\< タイムスタンプ > \Detail-Setup**)、末尾付近の次の警告が表示されます。  
  
`*** WARNING \*\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!  `
  
PDW で手動でこれらのステートメントを実行して、DMK を回復するために、その後アプライアンスを再起動してください。  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
」の手順を使用して、 **master データベースの復元**段落、データベースを回復し、アプライアンスを再起動します。  
  
DMK の前に存在していた操作の後は回復されなかった場合は、データベースが照会されたときに、次のエラー メッセージが生成されます。  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>パフォーマンスへの影響  
TDE のパフォーマンスに与える影響は、データの種類がある場合、格納方法と SQL Server PDW に対するワークロード アクティビティの種類によって異なります。 TDE で保護されているときに、I/O の読み取りとデータの暗号化を解除し、暗号化やデータを書き込むの CPU 処理を要するアクティビティでありと他の CPU 負荷の高いアクティビティが同時に発生しているときに複数の影響を及ぼします。 TDE で暗号化ため`tempdb`、TDE 暗号化されていないデータベースのパフォーマンスに影響することができます。 パフォーマンスを正確に把握を取得するには、データとクエリのアクティビティは、システム全体をテストする必要があります。  
  
## <a name="related-content"></a>関連コンテンツ  
次のリンクには、SQL Server が暗号化を管理する方法に関する一般的な情報が含まれています。 これらのトピックでは、SQL Server の暗号化がこれらのトピックに SQL Server PDW に固有の情報がないし、機能が SQL Server PDW に存在しませんが、についても説明を理解できます。  
  
-   [SQL Server の暗号化](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [暗号化階層](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [SQL Server とデータベースの暗号化キー](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>参照  
[ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md)  
[CREATE DATABASE ENCRYPTION KEY](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
