---
title: 別の SQL Server への TDE で保護されたデータベースの移動 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, moving
- TDE, moving a database
ms.assetid: fb420903-df54-4016-bab6-49e6dfbdedc7
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 42027a48803cd5269d5ab2d69452352bdbe62bc5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63012054"
---
# <a name="move-a-tde-protected-database-to-another-sql-server"></a>別の SQL Server への TDE で保護されたデータベースの移動
  このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)] を使用して、Transparent Data Encryption (TDE) によってデータベースを保護し、そのデータベースを別の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスに移動する方法について説明します。 TDE では、データとログ ファイルの暗号化および暗号化解除がリアルタイムの I/O で実行されます。 暗号化にはデータベース暗号化キー (DEK) が使用されます。これは、復旧時に使用できるようにデータベース ブート レコードに保存されます。 DEK とは、サーバーの `master` データベースに保存されている証明書を使用して保護される対称キー、または EKM モジュールによって保護される非対称キーのことです。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **透過的なデータ暗号化で保護されたデータベースを作成する方法:**  
  
     [SQL Server Management Studio](#SSMSCreate)  
  
     [Transact-SQL](#TsqlCreate)  
  
-   **データベースを移動する方法:**  
  
     [SQL Server Management Studio](#SSMSMove)  
  
     [Transact-SQL](#TsqlMove)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   TDE で保護されたデータベースを移動するとき、DEK を開くために使用される証明書または非対称キーも移動する必要があります。 証明書または非対称キーをインストールする必要があります、 `master` 、移行先サーバーのデータベースように[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース ファイルにアクセスできます。 詳細については、「[透過的なデータ暗号化 &#40;TDE&#41;](transparent-data-encryption.md)」を参照してください。  
  
-   証明書を復旧するために、証明書ファイルと秘密キー ファイルの両方のコピーを保持する必要があります。 秘密キーのパスワードは、データベース マスター キーのパスワードと同じにする必要はありません。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ここで作成されたファイルを格納**C:\Program files \microsoft SQL Server\MSSQL12 します。MSSQLSERVER\MSSQL\DATA**既定。 ただし、ファイル名と場所は異なる場合があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
  
-   必要があります`CONTROL DATABASE`に対する権限、`master`データベース マスター _ キーを作成するデータベース。  
  
-   必要があります`CREATE CERTIFICATE`に対する権限、 `master` DEK を保護する証明書を作成するデータベース。  
  
-   暗号化されたデータベースに対する `CONTROL DATABASE` 権限、およびデータベース暗号化キーの暗号化に使用する証明書または非対称キーに対する `VIEW DEFINITION` 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> 透過的なデータ暗号化で保護されたデータベースを作成するには  
  
###  <a name="SSMSCreate"></a> SQL Server Management Studio の使用  
  
1.  データベースのマスター _ キーを作成し、証明書、`master`データベース。 詳細については、「 **Transact-SQL の使用** 」をご覧ください。  
  
2.  サーバーの証明書のバックアップを作成、`master`データベース。 詳細については、「 **Transact-SQL の使用** 」をご覧ください。  
  
3.  オブジェクト エクスプローラーで、 **[データベース]** フォルダーを右クリックし、 **[新しいデータベース]** をクリックします。  
  
4.  **[新しいデータベース]** ダイアログ ボックスで、 **[データベース名]** ボックスに新しいデータベースの名前を入力します。  
  
5.  **[所有者]** ボックスに新しいデータベースの所有者を入力します。 または、省略記号 **[...]** をクリックして **[データベース所有者の選択]** ダイアログ ボックスを開きます。 新しいデータベースの作成の詳細については、「 [Create a Database](../../databases/create-a-database.md)」をご覧ください。  
  
6.  オブジェクト エクスプローラーで、プラス記号をクリックして **[データベース]** フォルダーを展開します。  
  
7.  作成したデータベースを右クリックし、 **[タスク]** をポイントし、 **[データベース暗号化の管理]** をクリックします。  
  
     **[データベース暗号化の管理]** ダイアログ ボックスでは、次のオプションを使用できます。  
  
     **暗号化アルゴリズム**  
     データベース暗号化で使用するアルゴリズムを表示または設定します。 既定の暗号化アルゴリズムは `AES128` です。 このフィールドを空白にすることはできません。 暗号化アルゴリズムの詳細については、「 [Choose an Encryption Algorithm](choose-an-encryption-algorithm.md)」をご覧ください。  
  
     **サーバー証明書の使用**  
     証明書によって保護するように暗号化を設定します。 一覧から選択します。 サーバー証明書に対する `VIEW DEFINITION` 権限がない場合、このリストは空になります。 証明書による暗号化方法が選択されている場合、この値を空にすることはできません。 証明書の詳細については、「 [SQL Server Certificates and Asymmetric Keys](../sql-server-certificates-and-asymmetric-keys.md)」をご覧ください。  
  
     **[サーバー非対称キーの使用]**  
     暗号化が非対称キーで保護されるように設定します。 使用可能な非対称キーのみが表示されます。 TDE を使用してデータベースを暗号化できるのは、EKM モジュールによって保護される非対称キーだけです。  
  
     **[データベース暗号化をオンに設定]**  
     データベースを変更して TDE をオンまたはオフにします。  
  
8.  完了したら、 **[OK]** をクリックします。  
  
###  <a name="TsqlCreate"></a> Transact-SQL の使用  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- Create a database master key and a certificate in the master database.  
    USE master ;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    CREATE CERTIFICATE TestSQLServerCert   
    WITH SUBJECT = 'Certificate to protect TDE key'  
    GO  
    -- Create a backup of the server certificate in the master database.  
    -- The following code stores the backup of the certificate and the private key file in the default data location for this instance of SQL Server   
    -- (C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA).  
  
    BACKUP CERTIFICATE TestSQLServerCert   
    TO FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Create a database to be protected by TDE.  
    CREATE DATABASE CustRecords ;  
    GO  
    -- Switch to the new database.  
    -- Create a database encryption key, that is protected by the server certificate in the master database.   
    -- Alter the new database to encrypt the database using TDE.  
    USE CustRecords;  
    GO  
    CREATE DATABASE ENCRYPTION KEY  
    WITH ALGORITHM = AES_128  
    ENCRYPTION BY SERVER CERTIFICATE TestSQLServerCert;  
    GO  
    ALTER DATABASE CustRecords  
    SET ENCRYPTION ON;  
    GO  
    ```  
  
 詳細については、以下をご覧ください。  
  
-   [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql)  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
-   [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
-   [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
##  <a name="TsqlProcedure"></a> データベースを移動するには  
  
###  <a name="SSMSMove"></a> SQL Server Management Studio の使用  
  
1.  オブジェクト エクスプローラーで、暗号化したデータベースを右クリックし、 **[タスク]** をポイントして **[デタッチ]** をクリックします。  
  
     **[データベースのデタッチ]** ダイアログ ボックスでは、次のオプションを使用できます。  
  
     **[デタッチするデータベース]**  
     デタッチするデータベースを一覧表示します。  
  
     **Database Name**  
     デタッチするデータベースの名前を表示します。  
  
     **[接続の削除]**  
     指定したデータベースへの接続を切断します。  
  
    > [!NOTE]  
    >  アクティブな接続があるデータベースをデタッチすることはできません。  
  
     **統計の更新**  
     既定では、データベースをデタッチしても、古い最適化統計情報が保持されます。既存の最適化統計情報を更新するには、このチェック ボックスをオンにします。  
  
     **[フルテキスト カタログの保持]**  
     既定では、デタッチ操作を行っても、データベースに関連付けられたフルテキスト カタログが保持されます。 これらのカタログを削除するには、 **[フルテキスト カタログの保持]** チェック ボックスをオフにします。 このオプションは、データベースを [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]からアップグレードする場合にのみ表示されます。  
  
     **ステータス**  
     次のどちらかの状態が表示されます: **[準備完了]** または **[準備ができていません]** 。  
  
     **メッセージ**  
     **[メッセージ]** 列に、次のようにデータベースに関する情報が表示される場合があります。  
  
    -   データベースがレプリケーションに含まれている場合、 **[状態]** は **[準備ができていません]** になり、 **[メッセージ]** 列に **[データベースがレプリケートされました]** と表示されます。  
  
    -   データベースに 1 つまたは複数のアクティブな接続、**状態**は**準備ができていません**と**メッセージ**列が表示されます _< number_of_active_connections>_ **アクティブな接続**- 例。 **[1 のアクティブな接続]** 。 データベースをデタッチするには、 **[接続の削除]** を選択してアクティブな接続を切断する必要があります。  
  
     メッセージについてより詳しい情報を得るには、ハイパーリンクのテキストをクリックして利用状況モニターを開きます。  
  
2.  **[OK]** をクリックします。  
  
3.  Windows エクスプローラーを使用して、移動元またはコピー元サーバーから移動先またはコピー先サーバーの同じ場所に、データベース ファイルを移動またはコピーします。  
  
4.  エクスプローラーを使用して、移動元またはコピー元サーバーから移動先またはコピー先サーバーの同じ場所に、サーバー証明書と秘密キー ファイルのバックアップを移動またはコピーします。  
  
5.  移動先またはコピー先の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスに、データベース マスター キーを作成します。 詳細については、「 **Transact-SQL の使用** 」をご覧ください。  
  
6.  元のサーバー証明書のバックアップ ファイルを使用して、サーバー証明書を再作成します。 詳細については、「 **Transact-SQL の使用** 」をご覧ください。  
  
7.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のオブジェクト エクスプローラーで、 **[データベース]** フォルダーを右クリックし、 **[アタッチ]** をクリックします。  
  
8.  **[データベースのインポート]** ダイアログ ボックスで、 **[アタッチするデータベース]** の下の **[追加]** をクリックします。  
  
9. **データベース ファイルの検索 -** _server_name_ダイアログ ボックスで、新しいサーバーにアタッチし、をクリックする、データベース ファイルを選択**OK**します。  
  
     **[データベースのインポート]** ダイアログ ボックスでは、次のオプションを使用できます。  
  
     **[アタッチするデータベース]**  
     選択されたデータベースに関する情報を表示します。  
  
     \<空白の列ヘッダー>  
     アタッチ操作の状態を示すアイコンが表示されます。 表示されるアイコンの種類は、下の **[状態]** の説明に示します。  
  
     **[MDF ファイルの場所]**  
     選択した MDF ファイルのパスとファイル名が表示されます。  
  
     **データベース名**  
     データベースの名前が表示されます。  
  
     **[次の名前でアタッチ]**  
     データベースを別の名前でアタッチする場合に、その名前を指定します。  
  
     **[所有者]**  
     データベースの所有者のドロップダウン リストです。これを使用して、必要に応じて別の所有者を選択できます。  
  
     **ステータス**  
     次の表に示すように、データベースの状態を表示します。  
  
    |アイコン|状態テキスト|説明|  
    |----------|-----------------|-----------------|  
    |(アイコンなし)|(テキストなし)|このオブジェクトのアタッチ操作が開始されていないか、保留されています。 これは、ダイアログ ボックスを開いたときの既定の状態です。|  
    |緑の右向き三角形|[実行中]|アタッチ操作が開始されましたが、完了していません。|  
    |緑のチェック マーク|成功|オブジェクトは正常にアタッチされました。|  
    |赤い丸の中に白い×印|[エラー]|アタッチ操作でエラーが発生し、正常に完了しませんでした。|  
    |4 つに区切られた丸印 (左右の領域が黒、上下の領域が白)|停止|ユーザーがアタッチ操作を停止したため、正常に完了しませんでした。|  
    |丸の中に反時計回りの矢印|[ロールバックされました]|アタッチ操作は正常に完了しましたが、他のオブジェクトのアタッチ中にエラーが発生したため、ロールバックされました。|  
  
     **メッセージ**  
     空白のメッセージ、または "ファイルが見つかりません" のハイパーリンクが表示されます。  
  
     **[追加]**  
     主な必須データベース ファイルを検索します。 ユーザーが .mdf ファイルを選択した場合、 **[アタッチするデータベース]** グリッドの対応するフィールドに、対応する情報が自動的に入力されます。  
  
     **[削除]**  
     選択したファイルを **[アタッチするデータベース]** グリッドから削除します。  
  
     **"** _<database_name>_ **" データベースの詳細**  
     デタッチするファイルの名前を表示します。 ファイルのパス名を確認または変更するには、**参照**ボタン ( **[...]** ) をクリックしてください。  
  
    > [!NOTE]  
    >  ファイルが存在しなかった場合、 **[メッセージ]** 列に "見つかりませんでした" と表示されます。 ログ ファイルが見つからない場合は、ログ ファイルが別のディレクトリに置かれているか、削除されています。 **[データベースの詳細]** グリッドでファイル パスを更新し、正しい場所を指定するか、そのログ ファイルをグリッドから削除します。 .ndf データ ファイルが見つからない場合、グリッドのパスを更新して、正しい場所を指定する必要があります。  
  
     **[元のファイル名]**  
     データベースに属している、アタッチされたファイルの名前が表示されます。  
  
     **[ファイルの種類]**  
     ファイルの種類を表します。 **[データ]** または **[ログ]** になります。  
  
     **[現在のファイル パス]**  
     選択されているデータベース ファイルのパスを表示します。 このパスは手作業で編集できます。  
  
     **メッセージ**  
     空白のメッセージ、または **"ファイルが見つかりません"** ハイパーリンクが表示されます。  
  
###  <a name="TsqlMove"></a> Transact-SQL の使用  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- Detach the TDE protected database from the source server.   
    USE master ;  
    GO  
    EXEC master.dbo.sp_detach_db @dbname = N'CustRecords';  
    GO  
    -- Move or copy the database files from the source server to the same location on the destination server.   
    -- Move or copy the backup of the server certificate and the private key file from the source server to the same location on the destination server.   
    -- Create a database master key on the destination instance of SQL Server.   
    USE master;  
    GO  
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '*rt@40(FL&dasl1';  
    GO  
    -- Recreate the server certificate by using the original server certificate backup file.   
    -- The password must be the same as the password that was used when the backup was created.  
  
    CREATE CERTIFICATE TestSQLServerCert   
    FROM FILE = 'TestSQLServerCert'  
    WITH PRIVATE KEY   
    (  
        FILE = 'SQLPrivateKeyFile',  
        DECRYPTION BY PASSWORD = '*rt@40(FL&dasl1'  
    );  
    GO  
    -- Attach the database that is being moved.   
    -- The path of the database files must be the location where you have stored the database files.  
    CREATE DATABASE [CustRecords] ON   
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords.mdf' ),  
    ( FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\CustRecords_log.LDF' )  
    FOR ATTACH ;  
    GO  
    ```  
  
 詳細については、以下をご覧ください。  
  
-   [sp_detach_db &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-detach-db-transact-sql)  
  
-   [CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql)  
  
-   [CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql)  
  
-   [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
## <a name="see-also"></a>参照  
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../databases/database-detach-and-attach-sql-server.md)  
  
  
