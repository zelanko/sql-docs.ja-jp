---
title: Parallel Data Warehouse の transparent data encryption |Microsoft Docs
description: Transparent data encryption (TDE) の並列データ ウェアハウス (PDW) 実行リアルタイム I/O 暗号化と、データとトランザクション ログ ファイルと、特殊な PDW ログ ファイルの復号化します。"
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 582c237819dab5f0a1e30e2bd4e27fe3cc9ae57f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959980"
---
# <a name="transparent-data-encryption"></a>透過的なデータ暗号化
データベースをセキュリティで保護するために、安全なシステムの設計、機密資産の暗号化、データベース サーバーに対するファイアウォールの構築などの予防策を講じることができます。 ただし、物理メディア (ドライブやバックアップ テープ) などが盗まれるシナリオで悪意のあるパーティできますだけ復元またはデータベースをアタッチし、データを参照します。 解決策の 1 つは、データベース内の機密データを暗号化し、データの暗号化に使用されるキーを証明書で保護することです。 これにより、キーを持たない人物によるデータの使用を防止できますが、このような保護は事前に計画する必要があります。  
  
*Transparent data encryption* (TDE) は、データのリアルタイム I/O 暗号化と解読を実行します。 ファイルとトランザクション ログ ファイルと特殊な PDW のログ ファイル。 暗号化にはデータベース暗号化キー (DEK) が使用されます。これは、復旧時に使用できるようにデータベース ブート レコードに保存されます。 DEK は、SQL Server の PDW の master データベースに格納されている証明書を使用してセキュリティで保護された対称キーです。 TDE では、"静止した" データ、つまりデータとログ ファイルが保護されます。 この暗号化は、法律、規制、およびさまざまな業界で確立されているガイドラインの多くに準拠できるようになっています。 この機能は、ソフトウェア開発者は既存のアプリケーションを変更することがなく AES および 3 des 暗号化アルゴリズムを使用してデータを暗号化できます。  
  
> [!IMPORTANT]  
> TDE では、クライアントと PDW 間を移動するデータの暗号化は提供されません。 クライアントと SQL Server PDW の間でデータを暗号化する方法の詳細については、次を参照してください。[証明書を準備](provision-certificate.md)します。  
>   
> TDE では、移動中、または使用中のデータは暗号化されません。 SQL Server の PDW 内の PDW コンポーネント間の内部トラフィックは暗号化されません。 メモリ バッファーに一時的に格納されたデータは暗号化されません。 このリスクを軽減するには、物理的にアクセスし、SQL Server の PDW への接続を制御します。  
  
セキュリティで保護されたデータベースは、正しい証明書を使用することで復元できます。  
  
> [!NOTE]  
> Tde 証明書を作成するときにする必要がありますすぐにバックアップして、関連付けられている秘密キーと共にします。 証明書が使用できなくなった場合、またはデータベースを別のサーバーに復元またはアタッチする必要がある場合に、証明書と秘密キーの両方のバックアップが必要です。これらのバックアップがない場合は、データベースを開けません。 暗号化証明書は、データベースで TDE を無効にした場合でも保持する必要があります。 データベースが暗号化されていない場合でも、トランザクション ログの一部はまだ保護されたままである場合があるため、データベースの完全バックアップが実行されるまでは、一部の操作では証明書が必要な場合があります。 有効期限の日付を過ぎた証明書であっても、TDE によりデータを暗号化および暗号化解除できる場合があります。  
  
データベース ファイルの暗号化は、ページ レベルで実行されます。 暗号化されたデータベースのページは、ディスクに書き込まれる前に暗号化され、メモリに読み込まれるときに暗号化解除されます。 TDE では、暗号化されたデータベースのサイズが増えることはありません。  
  
次の図は、TDE 暗号化キーの階層を示しています。  
  
![階層を表示します](media/tde-architecture.png "TDE_Architecture")  
  
## <a name="using-tde"></a>Transparent Data Encryption を使用します。  
TDE を使用するには、次の手順を実行します。 最初の 3 つの手順は TDE をサポートする SQL Server PDW を準備するときに、1 回のみ行われます。  
  
1.  Master データベースのマスター _ キーを作成します。  
  
2.  使用**sp_pdw_database_encryption** SQL Server PDW で TDE を有効にします。 この操作は、将来の一時的なデータの保護を確保するために、一時的なデータベースを変更し、一時テーブルを持つアクティブなセッションがある場合に試行した場合は失敗します。 **sp_pdw_database_encryption** PDW システム ログでユーザー データのマスキングをオンにします。 (ユーザー データのマスキング PDW システム ログの詳細については、次を参照してください[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)。)。  
  
3.  使用[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)認証および証明書のバックアップが格納される共有への書き込みできる資格情報を作成します。 目的の記憶域サーバーの資格情報が既に存在する場合は、既存の資格情報を使用することができます。  
  
4.  Master データベースでは、マスター _ キーによって保護された証明書を作成します。  
  
5.  記憶域共有に、証明書をバックアップします。  
  
6.  ユーザー データベースでは、データベース暗号化キーを作成し、master データベースに格納されている証明書によって保護します。  
  
7.  使用して、 `ALTER DATABASE` TDE を使用してデータベースを暗号化するステートメント。  
  
次の例の暗号化、`AdventureWorksPDW2012`という証明書を使用してデータベース`MyServerCert`SQL Server PDW で作成された。  
  
**まずは：SQL Server PDW で TDE を有効にします。** このアクションは、1 回でのみ必要です。  
  
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
  
**1 秒:作成し、master データベース内の証明書をバックアップします。** このアクションは、のみ 1 回必要です。 (推奨)、データベースごとに別の証明書をも、1 つの証明書で複数のデータベースを保護することができます。  
  
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
  
**前の：DEK を作成し、ユーザー データベースを暗号化する ALTER DATABASE を使用します。** このアクションは、TDE で保護されているデータベースごとに繰り返されます。  
  
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
  
暗号化と復号化の操作は、SQL Server によってバック グラウンド スレッドでスケジュールされます。 この記事の後半で表示される一覧で、カタログ ビューと動的管理ビューを使用してこれらの操作の状態を表示することができます。  
  
> [!CAUTION]  
> TDE が有効になっているデータベースのバックアップ ファイルも、データベース暗号化キーを使用して暗号化されます。 このため、このバックアップを復元するときには、データベース暗号化キーを保護している証明書が必要です。 つまり、データの損失を防ぐには、データベースをバックアップするだけでなく、サーバー証明書のバックアップも確実に保守する必要があります。 証明書が使用できなくなると、データの損失が発生します。  
  
## <a name="commands-and-functions"></a>コマンドと関数  
TDE の証明書を次に示すステートメントで処理できるようにするには、この証明書をデータベース マスター キーで暗号化する必要があります。  
  
次の表に、TDE のコマンドと関数の説明とリンクを示します。  
  
|コマンドまたは関数|目的|  
|-----------------------|-----------|  
|[データベース暗号化キーを作成します。](../t-sql/statements/create-database-encryption-key-transact-sql.md)|データベースの暗号化に使用されるキーを作成します。|  
|[データベース暗号化キーを変更します](../t-sql/statements/alter-database-encryption-key-transact-sql.md)|データベースの暗号化に使用されるキーを変更します。|  
|[データベース暗号化キーを削除します](../t-sql/statements/drop-database-encryption-key-transact-sql.md)|データベースの暗号化に使用されたキーを削除します。|  
|[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)|TDE を有効にするために使用される **ALTER DATABASE** オプションについて説明します。|  
  
## <a name="catalog-views-and-dynamic-management-views"></a>カタログ ビューと動的管理ビュー  
次の表に、TDE のカタログ ビューと動的管理ビューを示します。  
  
|カタログ ビューまたは動的管理ビュー|目的|  
|-------------------------------------------|-----------|  
|[sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md)|データベース情報を表示するカタログ ビュー|  
|[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)|データベース内の証明書を表示するカタログ ビュー|  
|[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)|データベース、およびデータベースの暗号化の状態で使用される暗号化キーについて、各ノードの情報を提供する動的管理ビュー。|  
  
## <a name="permissions"></a>アクセス許可  
TDE の各機能とコマンドには、上の表で説明されているように、個別の権限要件があります。  
  
TDE に関係するメタデータを表示する必要があります、`CONTROL SERVER`権限。  
  
## <a name="considerations"></a>考慮事項  
データベース暗号化操作の再暗号化スキャンが実行されている間は、データベースに対するメンテナンス操作が無効になります。  
  
使用してデータベース暗号化の状態を確認することができます、 **sys.dm_pdw_nodes_database_encryption_keys**動的管理ビュー。 詳細については、次を参照してください。、*カタログ ビューおよび動的管理ビュー*この記事の前半の「します。  
  
### <a name="restrictions"></a>制限  
中に、次の操作は許可されていません、 `CREATE DATABASE ENCRYPTION KEY`、 `ALTER DATABASE ENCRYPTION KEY`、 `DROP DATABASE ENCRYPTION KEY`、または`ALTER DATABASE...SET ENCRYPTION`ステートメント。  
  
-   データベースの削除。  
  
-   使用して、`ALTER DATABASE`コマンド。  
  
-   データベースのバックアップを開始しています。  
  
-   データベースの復元を開始しています。  
  
次の操作または条件により、 `CREATE DATABASE ENCRYPTION KEY`、 `ALTER DATABASE ENCRYPTION KEY`、 `DROP DATABASE ENCRYPTION KEY`、または`ALTER DATABASE...SET ENCRYPTION`ステートメント。  
  
-   `ALTER DATABASE`コマンドを実行します。  
  
-   データ バックアップが実行されている。  
  
データベース ファイルを作成する際には、TDE が有効になっているとファイルの瞬時初期化を使用できません。  
  
### <a name="areas-not-protected-by-tde"></a>TDE で保護されていない領域  
TDE では、外部テーブルは保護されません。  
  
TDE は、診断セッションを保護しません。 ユーザーが注意する必要があります使用中の診断セッション中に機密性の高いパラメーターを持つクエリにありません。 不要にするとすぐに、機密情報を表示する診断セッションを削除する必要があります。  
  
SQL Server PDW のメモリに配置すると、TDE で保護されたデータは復号化します。 アプライアンス上に特定の問題が発生した場合は、メモリ ダンプが作成されます。 問題の外観の時に、メモリのファイルは、コンテンツをダンプし、暗号化されていない形式で機密データを含めることができます。 他のユーザーと共有される前に、メモリ ダンプの内容を確認する必要があります。  
  
Master データベースが TDE で保護されていません。 Master データベースにユーザー データが含まれていないがログイン名などの情報には含まれています。  
  
### <a name="transparent-data-encryption-and-transaction-logs"></a>Transparent Data Encryption とトランザクション ログ  
TDE に使用するデータベースを有効にすると、次の仮想トランザクション ログを強制的に、仮想トランザクション ログの残りの部分の領域の解放の効果があります。 これにより、データベースが暗号化対象として設定された後にトランザクション ログにクリア テキストが残らないことが保証されます。 表示することによって、PDW の各ノードでログ ファイルの暗号化の状態を見つけることができます、`encryption_state`内の列、`sys.dm_pdw_nodes_database_encryption_keys`この例のように、ビュー。  
  
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
SQL Server PDW では、一連のトラブルシューティングのログを保持します。 (注、これは、トランザクション ログ、SQL Server エラー ログで、または Windows イベント ログでありません。)これらの PDW アクティビティ ログは、一部のユーザー データを含めることができます、クリア テキストで、完全なステートメントを含めることができます。 一般的な例として**挿入**と**UPDATE**ステートメント。 ユーザー データのマスキングは明示的に有効にオンまたはオフを使用して**sp_pdw_log_user_data_masking**します。 保護するための PDW アクティビティ ログ内のユーザー データのマスキングに自動的に SQL Server PDW での暗号化を有効にするとします。 **sp_pdw_log_user_data_masking** TDE を使用しない場合、ステートメントをマスクするためも使用できますが、問題を分析する、Microsoft サポート チームの機能を大幅に減るためは推奨されません。  
  
### <a name="transparent-data-encryption-and-the-tempdb-system-database"></a>Transparent Data Encryption と tempdb システム データベース  
使用して暗号化が有効にすると、tempdb システム データベースが暗号化されて[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)します。 これは、機能は、任意のデータベースが TDE を使用する前に必要です。 これには、SQL Server PDW の同じインスタンスで暗号化されていないデータベースのパフォーマンスに影響があります。  
  
## <a name="key-management"></a>キー管理  
データベース暗号化キー (DEK) は、master データベースに格納されている証明書によって保護されます。 これらの証明書は、master データベースのデータベース マスター_キー (DMK) によって保護されます。 DMK は、TDE で使用するには、サービス マスター _ キー (SMK) で保護する必要があります。  
  
(パスワードを提供する) などの人間の介入を必要とせず、システムは、キーにアクセスできます。 証明書を使用できない場合は、適切な証明書が利用可能になるまで、DEK を解読できませんを示すエラー メッセージが出力されます。  
  
保護する証明書を使用する間、1 つのアプライアンスからデータベースを移動する場合、' DEK をまず移行先サーバーで復元する必要があります。 通常どおり、データベースを復元できます。 詳細についてで、標準の SQL Server のドキュメントを参照してください。 [TDE で保護されたデータベースを別の SQL Server に移動](https://technet.microsoft.com/library/ff773063.aspx)します。  
  
それらを使用するデータベースのバックアップがある限り、Dek の暗号化に使用される証明書を保持する必要があります。 証明書のバックアップは、データベースの復元の秘密キーのない証明書を使用できないために、証明書の秘密キーを含める必要があります。 これらの証明書の秘密キー バックアップは、証明書の復元を指定する必要がありますパスワードで保護された別のファイルに格納されます。  
  
## <a name="restoring-the-master-database"></a>Master データベースを復元します。  
使用して、master データベースを復元できます**DWConfig**、ディザスター リカバリーの一部として。  
  
-   コントロールのノードが変更されていない場合は、DMK とすべての証明書を追加の操作なしで読み取り可能なされます元の master データベースのバックアップが行われた変更と同じアプライアンス上、master データベースを復元すると場合、です。  
  
-   異なるアプライアンスでは、master データベースを復元する場合、または制御ノードは master データベースのバックアップ以降に変更されている場合は、追加の手順は、DMK を再生成するために必要になります。  
  
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
  
## <a name="upgrade-and-replacing-virtual-machines"></a>アップグレードと仮想マシンを置き換える  
DMK がアップグレードまたは置換の VM が実行されたアプライアンス上に存在する場合は、パラメーターとして DMK のパスワードを指定する必要があります。  
  
アップグレード アクションの例です。 置換`**********`DMK パスワードを使用します。  
  
`setup.exe /Action=ProvisionUpgrade ... DMKPassword='**********'`  
  
仮想マシンを置換するアクションの例です。  
  
`setup.exe /Action=ReplaceVM ... DMKPassword='**********'`  
  
アップグレード中に、ユーザー データベースが暗号化されており、DMK パスワードが指定されていない場合、アップグレード アクションは失敗します。 置換、中に、DMK が存在する場合は、正しいパスワードが指定されていない操作がその DMK 復旧手順をスキップします。 その他のすべての手順は、アクションを追加の手順が必要なことを示すために、最後にエラーが報告されますが、置換 VM アクションの最後に完了できません。 セットアップ ログで (である **\ProgramData\Microsoft\Microsoft SQL Server Parallel Data Warehouse\100\Logs\Setup\\< タイムスタンプ > \Detail-Setup**)、末尾付近に次の警告が表示されます。  
  
`*** WARNING \*\*\* DMK is detected in master database, but could not be recovered automatically! The DMK password was either not provided or is incorrect!`
  
PDW で手動でこれらのステートメントを実行し、DMK を復旧するには、その後アプライアンスを再起動します。  
  
```sql
OPEN MASTER KEY DECRYPTION BY PASSWORD = '<DMK password>';  
ALTER MASTER KEY ADD ENCRYPTION BY SERVICE MASTER KEY;  
```
  
」の手順に従って、 **master データベースの復元**段落に、データベースを回復し、アプライアンスを再起動します。  
  
DMK は、前に存在して、アクションの後に回復されませんでした、データベースが照会されたときに、次のエラー メッセージが生成されます。  
  
```sql
Msg 110806;  
A distributed query failed: Database '<db_name>' cannot be opened due to inaccessible files or insufficient memory or disk space. See the SQL Server errorlog for details.
```  
  
## <a name="performance-impact"></a>パフォーマンスへの影響  
TDE のパフォーマンスに与える影響の種類のデータを格納する方法と、SQL Server PDW に対するワークロード アクティビティの種類によって異なります。 TDE で保護されていると読み取りデータの暗号化を解除または暗号化と、データの書き込みの I/O が CPU の処理を要するアクティビティと同時に他の CPU 負荷の高いアクティビティが発生しているときに、複数の影響を与えます。 TDE で暗号化されるため`tempdb`TDE が暗号化されていないデータベースのパフォーマンスに影響することができます。 パフォーマンスの正確なアイデアを取得するには、データとクエリのアクティビティは、システム全体をテストする必要があります。  
  
## <a name="related-content"></a>関連コンテンツ  
次のリンクには、SQL Server が暗号化を管理する方法について一般的な情報が含まれて。 これらの記事は、SQL Server の暗号化がこれらの記事には SQL Server PDW に固有の情報がないと、SQL Server PDW ではない機能についても説明を理解するのに役立ちます。  
  
-   [SQL Server の暗号化](../relational-databases/security/encryption/sql-server-encryption.md)  
  
-   [暗号化階層](../relational-databases/security/encryption/encryption-hierarchy.md)  
  
-   [SQL Server とデータベースの暗号化キー](../relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine.md)  

  
## <a name="see-also"></a>参照  
[ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md)  
[データベース暗号化キーを作成します。](../t-sql/statements/create-database-encryption-key-transact-sql.md)  
[BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[sp_pdw_database_encryption_regenerate_system_keys](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
[sp_pdw_log_user_data_masking](../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
[sys.certificates](../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[sys.dm_pdw_nodes_database_encryption_keys](../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-database-encryption-keys-transact-sql.md)  
  
