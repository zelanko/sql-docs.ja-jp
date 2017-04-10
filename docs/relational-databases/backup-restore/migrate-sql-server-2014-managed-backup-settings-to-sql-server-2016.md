---
title: "SQL Server 2014 マネージ バックアップの設定を SQL Server 2016 に移行する | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae937ebb-24ff-4a33-be3c-8f85328dfc75
caps.latest.revision: 7
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 6
---
# SQL Server 2014 マネージ バックアップの設定を SQL Server 2016 に移行する
  このトピックでは、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] から [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] にアップグレードする際の [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]の移行に関する考慮事項について説明します。  
  
 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] のプロシージャと基になる動作は [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]で変更されています。 次のセクションで、機能の変更点とその関連事項について説明します。  
  
## 概要  
 次の表では、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] に関する [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] と [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]の主要な機能の違いの一部について説明します。  
  
|領域|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|----------|---------------------------|---------------------------|  
|**名前空間:**|smart_admin|managed_backup|  
|**システム ストアド プロシージャ:**|sp_set_db_backup<br /><br /> sp_set_instance_backup|[sp_backup_config_basic](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)<br /><br /> [sp_backup_config_advanced](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-advanced-transact-sql.md)<br /><br /> [sp_backup_config_schedule](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)|  
|**セキュリティ:**|Microsoft Azure ストレージ アカウントとアクセス キーを使用した SQL 資格情報。|Microsoft Azure Shared Access Signature (SAS) トークンを使用した SQL 資格情報。|  
|**基になるストレージ:**|ページ BLOB を使用した Microsoft Azure Storage。|ブロック BLOB を使用した Microsoft Azure Storage。|  
  
## 利点  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]の新機能の使用には、いくつかの利点があります。  
  
-   ブロック BLOB により、格納のコストを抑えることができます。  
  
-   ストライピングを使用すると、はるかに大きなバックアップを格納できます (12 TB。一方のページ BLOB では 1 TB)。  
  
-   ストライピングにより、大規模データベースの復元時間も向上します。  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] での [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] のその他の機能強化については、「[Microsoft Azure への SQL Server マネージ バックアップ](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)」をご覧ください。  
  
## 考慮事項  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]からアップグレードした後、 [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] に関する次の考慮事項に注意してください。  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] で以前に [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] 用に構成したすべてのデータベースは、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] で **smart_admin** のシステム プロシージャと基になる動作を引き続き使用します。  
  
-   **smart_admin** のプロシージャは、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] の [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] の新しい構成ではサポートされません。 新しい **managed_backup** のプロシージャと機能を使用する必要があります。  
  
## 参照  
 [Microsoft Azure への SQL Server マネージ バックアップ](../../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)  
  
  