---
title: デバイスからのバックアップ復元 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4834a25b9100a37e027d8174897d86655c3690d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "70154739"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a>デバイスからのバックアップ復元 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、バックアップをデバイスから復元する方法について説明します。  
  
> [!NOTE]  
>  Azure Blob ストレージサービスへの SQL Server のバックアップの詳細については、「」 SQL Server、「 [Azure Blob Storage サービスを使用したバックアップと復元](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **次のものを使用してデバイスからバックアップを復元するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 復元するデータベースが存在しない場合、ユーザーは RESTORE を実行できる CREATE DATABASE 権限を使用する必要があります。 データベースが存在する場合、既定では、RESTORE 権限は **sysadmin** 固定サーバー ロールおよび **dbcreator** 固定サーバー ロールのメンバーと、データベースの所有者 (**dbo**) に与えられています (FROM DATABASE_SNAPSHOT オプションを使用する場合、データベースは常に存在します)。  
  
 RESTORE 権限は、サーバーでメンバーシップ情報を常に確認できるロールに与えられます。 固定データベース ロールのメンバーシップは、データベースがアクセス可能で破損していない場合にのみ確認することができますが、RESTORE の実行時にはデータベースがアクセス可能で損傷していないことが必ずしも保証されないため、 **db_owner** 固定データベース ロールのメンバーには RESTORE 権限は与えられません。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-restore-a-backup-from-a-device"></a>デバイスからバックアップを復元するには  
  
1.  の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]適切なインスタンスに接続した後、オブジェクトエクスプローラーで、サーバー名をクリックしてサーバーツリーを展開します。  
  
2.  [**データベース] を展開し**、データベースに応じて、ユーザーデータベースを選択するか、[**システムデータベース**] を展開してシステムデータベースを選択します。  
  
3.  データベースを右クリックして **[タスク]** をポイントし、 **[復元]** をクリックします。  
  
4.  実行する復元操作の種類 (**[データベース]**、 **[ファイルとファイル グループ]**、または **[トランザクション ログ]**) をクリックします。 対応する復元ダイアログ ボックスが開きます。  
  
5.  
  **[全般]** ページの **[復元用のソース]** セクションで、 **[デバイスから]** をクリックします。  
  
6.  
  **[デバイスから]** ボックスの参照ボタン ([...]) をクリックします。 **[バックアップの指定]** ダイアログ ボックスが開きます。  
  
7.  
  **[バックアップ メディア]** ボックスの一覧で、 **[バックアップ デバイス]** をクリックします。次に、 **[追加]** をクリックして **[バックアップ デバイスの選択]** ダイアログ ボックスを開きます。  
  
8.  
  **[バックアップ デバイス]** ボックスで、復元操作に使用するデバイスを選択します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-restore-a-backup-from-a-device"></a>デバイスからバックアップを復元するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  
  [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントで、バックアップ操作に使用する論理バックアップ デバイスまたは物理バックアップ デバイスを、次のように指定します。 この例は、物理名が `Z:\SQLServerBackups\AdventureWorks2012.bak`というディスク ファイルから復元します。  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a>参照  
 [RESTORE FILELISTONLY &#40;Transact-sql&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)   
 [RESTORE HEADERONLY &#40;Transact-sql&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)   
 [RESTORE LABELONLY &#40;Transact-sql&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-sql&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)   
 [Transact-sql&#41;&#40;単純復旧モデルでデータベースバックアップを復元する](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md)   
 [データベースバックアップを復元する &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md)   
 [データベースの差分バックアップを復元 &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md)   
 [SQL Server &#40;新しい場所にデータベースを復元&#41;](restore-a-database-to-a-new-location-sql-server.md)   
 [ファイルとファイルグループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [トランザクションログ &#40;SQL Server のバックアップ&#41;](back-up-a-transaction-log-sql-server.md)   
 [データベースの差分バックアップ &#40;SQL Server の作成&#41;](create-a-differential-database-backup-sql-server.md)  
  
  
