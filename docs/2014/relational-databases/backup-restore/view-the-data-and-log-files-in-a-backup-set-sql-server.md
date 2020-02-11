---
title: バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], viewing backup sets
- viewing backup set information
- backup sets [SQL Server], viewing files in
- displaying backup set information
- transaction log backups [SQL Server], viewing backup sets
- backing up [SQL Server], viewing backup sets
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fe58874e0046a53a33d0580c4477ac89f6cd6e18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62875051"
---
# <a name="view-the-data-and-log-files-in-a-backup-set-sql-server"></a>バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **バックアップセット内のデータファイルとログファイルを表示する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
 セキュリティについては、「[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)」を参照してください。  
  
####  <a name="Permissions"></a> Permissions  
 
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、バックアップ セットやバックアップ デバイスに関する情報の取得には CREATE DATABASE 権限が必要になります。 詳細については、「[GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a>バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示するには  
  
1.  の[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]適切なインスタンスに接続した後、オブジェクトエクスプローラーで、サーバー名をクリックしてサーバーツリーを展開します。  
  
2.  [**データベース] を展開し**、データベースに応じて、ユーザーデータベースを選択するか、[**システムデータベース**] を展開してシステムデータベースを選択します。  
  
3.  データベースを右クリックし、 **[プロパティ]** をクリックすると、 **[データベースのプロパティ]** ダイアログ ボックスが開きます。  
  
4.  
  **[ページの選択]** ペインの **[ファイル]** をクリックします。  
  
5.  
  **[データベース ファイル]** グリッドでデータとログ ファイルの一覧およびプロパティを確認します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a>バックアップ セットに含まれているデータ ファイルおよびログ ファイルを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  
  [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) ステートメントを使用します。 この例は、`FILE=2`バックアップ デバイスで 2 番目のバックアップ セット ( `AdventureWorksBackups` ) に関する情報を返します。  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [backupfilegroup &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql)   
 [backupfile &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql)   
 [backupset &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)   
 [backupmediaset &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql)   
 [backupmediafamily &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql)   
 [バックアップデバイス &#40;SQL Server&#41;](backup-devices-sql-server.md)  
  
  
