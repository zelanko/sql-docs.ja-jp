---
title: "論理バックアップ デバイスのプロパティと内容の表示 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バックアップ内容の表示"
  - "バックアップ内容の確認"
  - "データベース バックアップ [SQL Server], 内容の表示"
  - "データベースのバックアップ [SQL Server], 内容の表示"
  - "データベースのバックアップ [SQL Server], プロパティ"
  - "バックアップ プロパティの確認"
  - "情報を表示するバックアップ デバイス [SQL Server]"
  - "バックアップ プロパティの表示"
  - "データベースのバックアップ [SQL Server], プロパティ"
ms.assetid: 3a309074-e816-454d-b6c3-fcfdde0cbf74
caps.latest.revision: 22
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 22
---
# 論理バックアップ デバイスのプロパティと内容の表示 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]の論理バックアップ デバイスのプロパティと内容を表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **論理バックアップ デバイスのプロパティと内容を表示する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティについては、「[RESTORE LABELONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md)」を参照してください。  
  
####  <a name="Permissions"></a> 権限  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。 詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### 論理バックアップ デバイスのプロパティと内容を表示するには  
  
1.  オブジェクト エクスプローラーで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続した後、サーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[サーバー オブジェクト]**を展開し、 **[バックアップ デバイス]**を展開します。  
  
3.  デバイスをクリックし、**[プロパティ]** を右クリックして **[バックアップ デバイス]** ダイアログ ボックスを開きます。  
  
4.  **[全般]** ページにデバイス名とバックアップ先が表示されます。これはテープ ドライブまたはファイル パスです。  
  
5.  **[ページの選択]** ペインで **[メディアの内容]**をクリックします。  
  
6.  右側のペインに次のプロパティ パネルが表示されます。  
  
    -   **[メディア]**  
  
         メディアのシーケンス情報 (メディア シーケンス番号、ファミリ シーケンス番号、ミラー識別子など) とメディアの作成日時。  
  
    -   **[メディア セット]**  
  
         メディア セットの情報 (メディア セットの名前および説明) とメディア セット内のファミリ数。  
  
7.  **[バックアップ セット]** グリッドには、メディア セットの内容に関する情報が表示されます。  
  
> [!NOTE]  
>  詳細については、「[[バックアップ デバイス] ([メディアの内容] ページ)](../Topic/Backup%20Device%20\(Media%20Contents%20Page\).md)」を参照してください。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 論理バックアップ デバイスのプロパティと内容を表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  [RESTORE LABELONLY](../Topic/RESTORE%20LABELONLY%20\(Transact-SQL\).md) ステートメントを使用します。 この例は、`AdvWrks2008R2Backup` 論理バックアップ デバイスに関する情報を返します。  
  
```tsql  
USE AdventureWorks2012 ;  
RESTORE LABELONLY  
   FROM AdvWrks2008R2Backup ;  
GO  
  
```  
  
## 参照  
 [backupfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)   
 [backupfile &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [backupmediaset &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupmediafamily &#40;Transact-SQL&#41;](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [バックアップ デバイス &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
  