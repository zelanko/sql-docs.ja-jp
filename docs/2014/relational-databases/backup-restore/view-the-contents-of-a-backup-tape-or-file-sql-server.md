---
title: バックアップ テープまたはバックアップ ファイルの内容の表示 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- displaying backup content
- viewing backup content
- tape backup devices, viewing contents
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: dfee2d0f32ffaaf73527effdeea13d43b83a39fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62921229"
---
# <a name="view-the-contents-of-a-backup-tape-or-file-sql-server"></a>バックアップ テープまたはバックアップ ファイルの内容の表示 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]のバックアップ テープまたはバックアップ ファイルの内容を表示する方法について説明します。  
  
> [!NOTE]  
>  テープ バックアップ デバイスは、将来のバージョンの SQL Server でサポートされなくなる予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **バックアップテープまたはファイルの内容を表示する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティについては、「[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)」を参照してください。  
  
####  <a name="Permissions"></a> Permissions  
 
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。 詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a>バックアップ テープまたはバックアップ ファイルの内容を表示するには  
  
1.  の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]適切なインスタンスに接続した後、オブジェクトエクスプローラーで、サーバー名をクリックしてサーバーツリーを展開します。  
  
2.  [**データベース] を展開し**、データベースに応じて、ユーザーデータベースを選択するか、[**システムデータベース**] を展開してシステムデータベースを選択します。  
  
3.  バックアップするデータベースを右クリックし、 **[タスク]** をポイントして、 **[バックアップ]** をクリックします。 
  **[データベースのバックアップ]** ダイアログ ボックスが表示されます。  
  
4.  
  **[全般]** ページの **[バックアップ先]** セクションで、 **[ディスク]** または **[テープ]** のいずれかをクリックします。 
  **[バックアップ先]** ボックスの一覧で、ディスク ファイルまたはテープを検索します。  
  
     ディスク ファイルまたはテープがボックスの一覧に表示されない場合、 **[追加]** をクリックします。 ファイル名またはテープ ドライブを選択します。 
  **[バックアップ先]** ボックスの一覧に追加するには、 **[OK]** をクリックします。  
  
5.  
  **[バックアップ先]** ボックスの一覧で、表示するディスクまたはテープ ドライブのパスを選択し、 **[コンテンツ]** をクリックします。 これにより、 **[デバイス コンテンツ]** ダイアログ ボックスが開きます。  
  
6.  選択したテープまたはファイル上にあるメディア セットやバックアップ セットに関する情報が、右側のペインに表示されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a>バックアップ テープまたはバックアップ ファイルの内容を表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  
  [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) ステートメントを使用します。 この例は、 `AdventureWorks2012-FullBackup.bak`というファイルに関する情報を返します。  
  
```sql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [backupfilegroup &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)   
 [backupfile &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql)   
 [backupset &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [backupmediaset &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql)   
 [backupmediafamily &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)   
 [バックアップデバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)   
 [ディスクファイル &#40;SQL Server の論理バックアップデバイスを定義&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [テープドライブ &#40;SQL Server の論理バックアップデバイスを定義&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
