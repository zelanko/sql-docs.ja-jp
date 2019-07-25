---
title: データベースの完全バックアップの作成 (SQL Server) | Microsoft Docs
ms.custom: sqlfreshmay19
ms.date: 05/29/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], full backups
- backing up databases [SQL Server], SQL Server Management Studio
- backups [SQL Server], creating
- database backups [SQL Server], SQL Server Management Studio
ms.assetid: 586561fc-dfbb-4842-84f8-204a9100a534
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8888784d2adccddeb5b3f509b39803405d102efd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076064"
---
# <a name="create-a-full-database-backup-sql-server"></a>データベースの完全バックアップの作成 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../includes/tsql-md.md)]、または PowerShell を使用して、データベースの完全バックアップを作成する方法について説明します。  
  

Azure BLOB ストレージ サービスへの SQL Server のバックアップについては、「[Microsoft Azure BLOB ストレージ サービスを使用した SQL Server のバックアップと復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」および「[SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md)」を参照してください。  
  
##  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   BACKUP ステートメントは、明示的または暗黙的なトランザクションでは使用できません。    
-   新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって作成されたバックアップは、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では復元できません。   
-   バックアップの概念とタスクに関する概要および詳細については、先へ進む前に「[Backup Overview &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)」を参照してください。  
  
## <a name="Recommendations"></a> 推奨事項  
  
-   データベース サイズが大きくなると、データベースの完全バックアップにかかる時間は長くなり、必要な記憶領域も増加します。 大規模なデータベースでは、一連の[データベースの差分バックアップ](../../relational-databases/backup-restore/differential-backups-sql-server.md)を使用してデータベースの完全バックアップを補完することを検討してください。 詳細については、「 [SQL Server Backup to URL](../../relational-databases/backup-restore/sql-server-backup-to-url.md)」を参照してください。    
-   データベースの完全バックアップのサイズは、 [sp_spaceused](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md) システム ストアド プロシージャを使用して推計します。    
-   既定では、バックアップ操作が成功するたびに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログおよびシステム イベント ログにエントリが 1 つ追加されます。 頻繁にバックアップすると、これらの成功メッセージがすぐに蓄積され、エラー ログが大きくなります。 そのために、他のメッセージを探すのが困難になることがあります。 そのような場合、これらのエントリに依存するスクリプトがなければ、トレース フラグ 3226 を使用することによってこれらのバックアップ ログ エントリを除外できます。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」を参照してください。  
  
##  <a name="Security"></a> セキュリティ  
 データベースをバックアップすると、TRUSTWORTHY は OFF に設定されます。 TRUSTWORTHY を ON に設定する方法については「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)」を参照してください。  
  
 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降では、バックアップの作成での **PASSWORD** および **MEDIAPASSWORD** オプションが廃止されました。 パスワード付きで作成されたバックアップを復元することは、引き続き可能です。  
  
##  <a name="Permissions"></a> Permissions  
 BACKUP DATABASE 権限と BACKUP LOG 権限は、既定では、 **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_backupoperator** 固定データベース ロールのメンバーに与えられています。  
  
 バックアップ デバイスの物理ファイルに対する所有と許可の問題によって、バックアップ操作が妨げられることがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、デバイスに対して読み書きを実行できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスが実行されているアカウントには書き込み権限が **必要** です。 ただし、システム テーブルにバックアップ デバイスのエントリを追加する [sp_addumpdevice](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)では、ファイル アクセスの権限は確認されません。 バックアップ デバイスの物理ファイルに関するこのような問題は、バックアップや復元が試行され、物理リソースがアクセスされるまで、表面化しない可能性があります。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用してバックアップ タスクを指定する場合、 **[スクリプト]** ボタンをクリックしてスクリプトの保存先を選択することにより、対応する [!INCLUDE[tsql](../../includes/tsql-md.md)] [BACKUP](../../t-sql/statements/backup-transact-sql.md) スクリプトを生成できます。  
  
### <a name="back-up-a-database"></a>データベースをバックアップする  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]で適切な **オブジェクト エクスプローラー**のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。    
1.  **[データベース]** を展開し、ユーザー データベースを選択するか、または **[システム データベース]** を展開してシステム データベースを選択します。    
1.  データベースを右クリックして **[タスク]** をポイントし、 **[バックアップ]** をクリックします。 **[データベースのバックアップ]** ダイアログ ボックスが表示されます。  
1. ドロップダウン リストから **[データベース]** を選択します。 
1. **[バックアップの種類]** ボックスの一覧で、 **[完全]** を選択します。 
1. **[バックアップ コンポーネント]** で **[データベース]** を選択します。 
1. **[バックアップ先]** セクションでは、 **[バックアップ先]** ドロップダウン リストを使用してバックアップ先を選びます。 新しいバックアップ オブジェクトやバックアップ先を追加するには、 **[追加]** をクリックします。 バックアップ先を削除するには、バックアップ先を選択して **[削除]** をクリックします。 既存のバックアップ先の内容を表示するには、バックアップ先を選択して **[内容]** をクリックします。
1. (省略可能) **[メディア オプション]** と **[バックアップ オプション]** のページで、その他の使用可能な設定を確認します。 さまざまなバックアップ オプションの詳細については、[[全般] ページ](back-up-database-general-page.md)、[[メディア オプション] ページ](back-up-database-media-options-page.md)、[[バックアップ オプション] ページ](back-up-database-backup-options-page.md)を参照してください。 



### <a name="additional-information"></a>関連情報
- データベースの完全バックアップを作成すると、データベースの差分バックアップを作成できるようになります。詳細については、「[データベースの差分バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)」を参照してください。  
- 必要であれば、 **[コピーのみのバックアップ]** チェック ボックスをオンにして、コピーのみのバックアップを作成することもできます。 *コピーのみのバックアップ*は、従来の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップのシーケンスから独立した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップです。 詳細については、「[コピーのみのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/copy-only-backups-sql-server.md)」を参照してください。  コピーのみのバックアップは、 **[差分]** バックアップの種類には使用できません。  
- URL にバックアップする場合は、 **[メディア オプション]** ページで、 **[メディアに上書きします]** を無効にできます。 


## <a name="ssms-examples"></a>SSMS の例  

次の例では、次の Transact-SQL コードを使用してテスト データベースを作成します。

```sql
USE [master]
GO

CREATE DATABASE [SQLTestDB]
GO

USE [SQLTestDB]
GO
CREATE TABLE SQLTest (
    ID INT NOT NULL PRIMARY KEY,
    c1 VARCHAR(100) NOT NULL,
    dt1 DATETIME NOT NULL DEFAULT getdate()
)
GO


USE [SQLTestDB]
GO

INSERT INTO SQLTest (ID, c1) VALUES (1, 'test1')
INSERT INTO SQLTest (ID, c1) VALUES (2, 'test2')
INSERT INTO SQLTest (ID, c1) VALUES (3, 'test3')
INSERT INTO SQLTest (ID, c1) VALUES (4, 'test4')
INSERT INTO SQLTest (ID, c1) VALUES (5, 'test5')
GO

SELECT * FROM SQLTest
GO
```

### <a name="a-full-back-up-to-disk-to-default-location"></a>A. 既定の場所のディスクへの完全バックアップ
この例では、`SQLTestDB` データベースを既定のバックアップ場所にあるディスクにバックアップします。  `SQLTestDB` のバックアップはまだ作成されていません。
1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。
2.  **[データベース]** を展開して `SQLTestDB`を右クリックし、 **[タスク]** をポイントしてから **[バックアップ]** をクリックします。
3.  **[OK]** を選択します。

![SQL のバックアップを取得する](media/quickstart-backup-restore-database/backup-db-ssms.png) 
 

### <a name="b--full-back-up-to-disk-to-non-default-location"></a>**B.既定以外の場所のディスクへの完全バックアップ**
この例では、`SQLTestDB` データベースを `F:\MSSQL\BAK` にあるディスクにバックアップします。  `SQLTestDB` のバックアップは既に作成されています。
1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。
2.  **[データベース]** を展開して `Sales`を右クリックし、 **[タスク]** をポイントしてから **[バックアップ]** をクリックします。
3.  **[全般]** ページの **[バックアップ先]** セクションで、 **[バックアップ先]** ドロップダウン リストから **[ディスク]** を選択します。
4.  既存のバックアップ ファイルがすべて削除されるまで、 **[削除]** を選択します。
5.  **[追加]** を選択すると、 **[バックアップ先の選択]** ダイアログ ボックスが開きます。
6.  `F:\MSSQL\BAK\Sales_20160801.bak` [ファイル名] **テキスト ボックスに「** 」と入力します。
7.  **[OK]** を選択します。
8.  **[OK]** を選択します。

![DB の場所を変更する](media/create-a-full-database-backup-sql-server/change-db-location.png)

### <a name="c--create-an-encrypted-backup"></a>**C.暗号化されたバックアップの作成**
この例では、`SQLTestDB` データベースを暗号化して既定のバックアップ場所にバックアップします。  

1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。
1. **[新しいクエリ]** ウィンドウを開き、次のコマンドを実行して、`SQLTestDB` データベース内に[**データベース マスター キー**](../../relational-databases/security/encryption/create-a-database-master-key.md)と[**証明書**](../../t-sql/statements/create-certificate-transact-sql.md)を作成します。 

    ```sql
    USE [SQLTestDB]
        
    -- Create the database master key
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';  
    
    
    -- Create the certificate
    CREATE CERTIFICATE MyCertificate   
    ENCRYPTION BY PASSWORD = 'pGFD4bb925DGvbd2439587y'  
    EXPIRY_DATE = '20201031';  
    GO  
    ```

1.  **オブジェクト エクスプローラー**で、 **[データベース]** を展開して `SQLTestDB` を右クリックし、 **[タスク]** をポイントしてから **[バックアップ]** をクリックします。
1.  **[メディア オプション]** ページの **[メディアを上書きする]** セクションで、 **[新しいメディア セットにバックアップし、すべての既存のバックアップ セットを消去する]** をオンにします。
1.  **[バックアップ オプション]** ページの **[暗号化]** セクションで、 **[バックアップを暗号化する]** チェック ボックスをオンにします。
1.  [アルゴリズム] ボックスの一覧から、 **[AES 256]** を選択します。
1.  **[証明書または非対称キー]** ボックスの一覧で、 `MyCertificate`を選択します。
1.  **[OK]** を選択します。

![暗号化されたバックアップ](media/create-a-full-database-backup-sql-server/encrypted-backup.png)

### <a name="d--back-up-to-the-azure-blob-storage-service"></a>**D.Azure BLOB ストレージ サービスへのバックアップ**


次の 3 つの例では、Microsoft Azure BLOB ストレージ サービスへの `Sales` のデータベースの完全バックアップを実行します。  ストレージ アカウント名は `mystorageaccount`です。  コンテナーは `myfirstcontainer`と呼ばれます。  簡潔にするため、最初の 4 つの手順をここに一度だけリストし、例はすべて **手順 5.** から始めます。

1.  **オブジェクト エクスプローラー**で、SQL Server データベース エンジンのインスタンスに接続し、そのインスタンスを展開します。
2.  **[データベース]** を展開して `Sales`を右クリックし、 **[タスク]** をポイントしてから **[バックアップ]** をクリックします。
3.  **[全般]** ページの **[宛先]** セクションで、 **[バックアップ先]** ドロップダウン リストから **[URL]** を選択します。
4.  **[追加]** をクリックすると、 **[バックアップ先の選択]** ダイアログ ボックスが開きます。

#### <a name="striped-backup-to-url-and-a-sql-server-credential-already-exists"></a>URL へのストライプ バックアップで SQL Server 資格情報が既に存在する場合

保存されたアクセス ポリシーは読み取り、書き込み、および一覧表示権で作成されています。  SQL Server 資格情報 `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`は、保存されたアクセス ポリシーに関連付けられている Shared Access Signature を使用して作成されています。  

   5.   `https://mystorageaccount.blob.core.windows.net/myfirstcontainer` [Azure ストレージ コンテナー:] **テキスト ボックスから** を選択します。
   6.  **[バックアップ ファイル:]** テキスト ボックスに、「 `Sales_stripe1of2_20160601.bak`」と入力します。
   7.  **[OK]** をクリックします。
   8.  手順 **4.** と **5.** を繰り返します。
   9.  **[バックアップ ファイル:]** テキスト ボックスに、「 `Sales_stripe2of2_20160601.bak`」と入力します。
   10.  **[OK]** をクリックします。
   11.   **[OK]** をクリックします。

#### <a name="a-shared-access-signature-exists-and-a-sql-server-credential-does-not-exist"></a>Shared Access Signature は存在し、SQL Server 資格情報は存在しない場合

  5.    **[Azure ストレージ コンテナー:]** テキスト ボックスに「`https://mystorageaccount.blob.core.windows.net/myfirstcontainer`」と入力します。  
  6.    **[共有アクセス ポリシー:]** テキスト ボックスに Shared Access Signature を入力します。  
  7.    **[OK]** をクリックします。  
  8.    **[OK]** をクリックします。


#### <a name="a-shared-access-signature-does-not-exist"></a>Shared Access Signature が存在しない場合

  5.    **[新しいコンテナー]** ボタンをクリックすると、 **[Microsoft サブスクリプションへの接続]** ダイアログ ボックスが開きます。   
  6.    **[Microsoft サブスクリプションへの接続]** ダイアログ ボックスに入力し、 **[OK]** をクリックして **[バックアップ先の選択]** ダイアログ ボックスに戻ります。  詳細については、「 [Microsoft Azure サブスクリプションへの接続](../../relational-databases/backup-restore/connect-to-a-microsoft-azure-subscription.md) 」を参照してください。  
  7.    **[バックアップ先の選択]** ダイアログ ボックスで **[OK]** をクリックします。  
  8.    **[OK]** をクリックします。

  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
### <a name="create-a-full-database-backup"></a>データベースの完全バックアップの作成  
  
1.  次の項目を指定した BACKUP DATABASE ステートメントを実行し、データベースの完全バックアップを作成します。  
  
    -   バックアップするデータベースの名前。   
    -   データベースの完全バックアップを書き込むバックアップ デバイス。    
     データベースの完全バックアップのための [!INCLUDE[tsql](../../includes/tsql-md.md)] の基本構文を次に示します。  
  
     BACKUP DATABASE *database*  
       TO *backup_device* [ **,** ...*n* ]    
     [ WITH *with_options* [ **,** ...*o* ] ] ;  
  
    |オプション|[説明]|  
    |------------|-----------------|  
    |*database*|バックアップするデータベースです。|  
    |*backup_device* [ **,** ...*n* ]|バックアップ操作に使用する 1 ～ 64 個のバックアップ デバイスの一覧を指定します。 物理バックアップ デバイスを指定したり、対応する論理バックアップ デバイス (既に定義されている場合) を指定したりできます。 物理バックアップ デバイスを指定するには、DISK オプションまたは TAPE オプションを使用します。<br /><br /> { DISK &#124; TAPE } **=** _physical\_backup\_device\_name_<br /><br /> 詳細については、「 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)」を参照してください。|  
    |WITH *with_options* [ **,** ...*o* ]|必要に応じて、1 つ以上の追加オプション ( *o*) を指定します。 基本的な with オプションについては、手順 2. を参照してください。|  
  
2.  必要に応じて、1 つ以上の WITH オプションを指定します。 ここでは、一部の基本的な WITH オプションについて説明します。 すべての WITH オプションについては、「 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)」を参照してください。  

基本的なバックアップ セット WITH オプション

- **{ COMPRESSION | NO_COMPRESSION }** :[!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] 以降でのみ、このバックアップで [バックアップの圧縮](../../relational-databases/backup-restore/backup-compression-sql-server.md) を実行するかどうかを指定し、サーバー レベルの既定値をオーバーライドできます。 
- **ENCRYPTION (ALGORITHM,  SERVER CERTIFICATE |ASYMMETRIC KEY)** :SQL Server 2014 以降でのみ、使用する暗号化アルゴリズムと暗号化の保護に使用する証明書または非対称キーを指定します。
- **DESCRIPTION** **=** { **'** _text_ **'**  |  **@** _text\_variable_ }:バックアップ セットを記述したテキストを自由な形式で指定します。 文字列の長さは最大 255 文字です。  
- **NAME = { *backup_set_name* |  **@** _backup\_set\_name\_var_ }** :バックアップ セットの名前を指定します。 名前の長さは最大 128 文字です。 NAME を指定しないと、名前は空白になります。 
  
 
既定では、BACKUP はバックアップを既存のメディア セットに追加し、既存のバックアップ セットを保持します。 これを明示的に指定するには、NOINIT オプションを使用します。 既存のバックアップ セットへの追加については、「 [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。  

また、FORMAT オプションを使用して、バックアップ メディアをフォーマットすることもできます。  

FORMAT [ **,** MEDIANAME **=** { *media_name* |  **@** _media\_name\_variable_ } ] [ **,** MEDIADESCRIPTION **=** { *text* |  **@** _text\_variable_ } ]  
FORMAT 句は、バックアップ メディアを初めて使用する場合や既存のデータをすべて上書きする場合に使用します。 必要に応じて、新しいメディアにメディア名と説明を割り当てます。  

> [!IMPORTANT]  
>  BACKUP ステートメントで FORMAT 句を使用すると、バックアップ メディアに格納されているバックアップが破棄されるので、十分注意して使用してください。  
  
##  <a name="TsqlExample"></a> Transact-SQL の例  
次の例では、次の Transact-SQL コードを使用してテスト データベースを作成します。

```sql
USE [master]
GO

CREATE DATABASE [SQLTestDB]
GO

USE [SQLTestDB]
GO
CREATE TABLE SQLTest (
    ID INT NOT NULL PRIMARY KEY,
    c1 VARCHAR(100) NOT NULL,
    dt1 DATETIME NOT NULL DEFAULT getdate()
)
GO


USE [SQLTestDB]
GO

INSERT INTO SQLTest (ID, c1) VALUES (1, 'test1')
INSERT INTO SQLTest (ID, c1) VALUES (2, 'test2')
INSERT INTO SQLTest (ID, c1) VALUES (3, 'test3')
INSERT INTO SQLTest (ID, c1) VALUES (4, 'test4')
INSERT INTO SQLTest (ID, c1) VALUES (5, 'test5')
GO

SELECT * FROM SQLTest
GO
```
  
#### <a name="a-back-up-to-a-disk-device"></a>**A.ディスク デバイスへのバックアップ**  
 次の例では、新しいメディア セットを作成する `SQLTestDB` を使用して、 `FORMAT` データベース全体をディスクにバックアップします。  
  
```sql  
USE SQLTestDB;  
GO  
BACKUP DATABASE SQLTestDB  
TO DISK = 'Z:\SQLServerBackups\SQLTestDB.Bak'  
   WITH FORMAT,  
      MEDIANAME = 'Z_SQLServerBackups',  
      NAME = 'Full Backup of SQLTestDB';  
GO  
```  
  
#### <a name="b-back-up-to-a-tape-device"></a>**B.テープ デバイスへのバックアップ**  
 次の例では、 `SQLTestDB` データベース全体をテープにバックアップし、以前のバックアップに追加します。  
  
```sql  
USE SQLTestDB;  
GO  
BACKUP DATABASE SQLTestDB  
   TO TAPE = '\\.\Tape0'  
   WITH NOINIT,  
      NAME = 'Full Backup of SQLTestDB';  
GO  
```  
  
#### <a name="c-back-up-to-a-logical-tape-device"></a>**C.論理テープ デバイスへのバックアップ**  
 次の例では、テープ ドライブ用の論理バックアップ デバイスを作成した後、 そのデバイスに SQLTestDB データベース全体をバックアップします。  
  
```sql  
-- Create a logical backup device,   
-- SQLTestDB_Bak_Tape, for tape device \\.\tape0.  
USE master;  
GO  
EXEC sp_addumpdevice 'tape', 'SQLTestDB_Bak_Tape', '\\.\tape0'; USE SQLTestDB;  
GO  
BACKUP DATABASE SQLTestDB  
   TO SQLTestDB_Bak_Tape  
   WITH FORMAT,  
      MEDIANAME = 'SQLTestDB_Bak_Tape',  
      MEDIADESCRIPTION = '\\.\tape0',   
      NAME = 'Full Backup of SQLTestDB';  
GO  
```  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
**Backup-SqlDatabase** コマンドレットを使用します。 データベースの完全バックアップであることを明示するには、 **-BackupAction**  パラメーターにその既定値 **Database**を指定します。 このパラメーターは、データベースの完全バックアップでは省略可能です。  

## <a name="powershell-examples"></a>PowerShell の例

### <a name="a--full-local-backup"></a>A.  ローカルの完全バックアップ 
次の例では、 `MyDB` データベースの完全なバックアップを、サーバー インスタンス `Computer\Instance`の既定のバックアップ場所に作成します。 オプションで、この例では **-BackupAction Database** を指定します。  
```powershell 
Backup-SqlDatabase -ServerInstance Computer\Instance -Database MyDB -BackupAction Database  
```
 
### <a name="b--full-backup-to-microsoft-azure"></a>B.  Microsoft Azure への完全バックアップ 
次の例では、Microsoft Azure BLOB ストレージ サービスに `MyServer` インスタンスのデータベース `Sales` の完全バックアップを作成します。  保存されたアクセス ポリシーは読み取り、書き込み、および一覧表示権で作成されています。  SQL Server 資格情報 `https://mystorageaccount.blob.core.windows.net/myfirstcontainer`は、保存されたアクセス ポリシーに関連付けられている Shared Access Signature を使用して作成されています。  PowerShell コマンドでは **BackupFile** パラメーターを使用して、場所 (URL) とバックアップ ファイル名を指定します。

```powershell  
import-module sqlps;
$container = 'https://mystorageaccount.blob.core.windows.net/myfirstcontainer';
$FileName = 'Sales.bak';
$database = 'Sales';
$BackupFile = $container + '/' + $FileName ;
  
Backup-SqlDatabase -ServerInstance "MyServer" -Database $database -BackupFile $BackupFile;
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
- [SQL Server のバックアップと復元操作のトラブルシューティング](https://support.microsoft.com/kb/224071)
- [バックアップの概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-overview-sql-server.md)
- [トランザクション ログのバックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)
- [メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](../../relational-databases/backup-restore/media-sets-media-families-and-backup-sets-sql-server.md)
- [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)
- [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
- [データベースのバックアップ &#40;全般ページ&#41;](../../relational-databases/backup-restore/back-up-database-general-page.md)
- [データベースのバックアップ &#40;バックアップ オプション ページ&#41;](../../relational-databases/backup-restore/back-up-database-backup-options-page.md)
- [差分バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/differential-backups-sql-server.md)
- [データベースの完全バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-database-backups-sql-server.md)  
  
  
