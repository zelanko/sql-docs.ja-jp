---
title: "プライマリ ファイル グループと他のファイル グループを 1 つオフラインで復元する例 (完全復旧モデル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "完全復旧モデル [SQL Server], RESTORE の例"
  - "オフライン復元 [SQL Server]"
  - "復元シーケンス [SQL Server], オフライン"
ms.assetid: 7d6c50eb-dc84-4d66-855a-0b5f1bd89737
caps.latest.revision: 32
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 32
---
# プライマリ ファイル グループと他のファイル グループを 1 つオフラインで復元する例 (完全復旧モデル)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックは、複数のファイル グループを含む、完全復旧モデルのデータベースだけに関連しています。  
  
 この例では、`adb` というデータベースに 3 つのファイル グループが含まれているとします。 ファイル グループ `A` とファイル グループ `C` は読み取り/書き込みが可能で、ファイル グループ `B` は読み取り専用です。 プライマリ ファイル グループとファイル グループ `B` は破損していますが、ファイル グループ `A` とファイル グループ `C` は破損していません。 障害が発生する前は、すべてのファイル グループがオンラインになっていました。  
  
 データベース管理者は、プライマリ ファイル グループとファイル グループ `B` を復元および復旧することにしました。 データベースでは完全復旧モデルを使用しているため、復元を開始する前に、データベースのログ末尾のバックアップを作成する必要があります。 データベースがオンラインになると、ファイル グループ `A` とファイル グループ `C` は自動的にオンラインになります。  
  
> [!NOTE]  
>  オフライン復元シーケンスは、読み取り専用ファイルのオンライン復元の場合に比べ、少ない手順で済みます。 例については、「[例: 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)」を参照してください。 ただし、オフライン復元中は、データベース全体がオフラインになります。  
  
## ログ末尾のバックアップ  
 データベースの管理者は、データベースを復元する前に、ログの末尾をバックアップする必要があります。 データベースが破損しているため、ログ末尾のバックアップを作成するには、NO_TRUNCATE オプションを使用する必要があります。  
  
```  
BACKUP LOG adb TO tailLogBackup   
   WITH NORECOVERY, NO_TRUNCATE  
```  
  
 ログ末尾のバックアップは、次の復元シーケンスの最後に適用されます。  
  
## 復元シーケンス  
 プライマリ ファイル グループとファイル グループ `B` を復元するために、データベース管理者は、次に示すように、PARTIAL オプションを使用せずに復元シーケンスを使用します。  
  
```  
RESTORE DATABASE adb FILEGROUP='Primary' FROM backup1   
WITH NORECOVERY  
RESTORE DATABASE adb FILEGROUP='B' FROM backup2   
WITH NORECOVERY  
RESTORE LOG adb FROM backup3 WITH NORECOVERY  
RESTORE LOG adb FROM backup4 WITH NORECOVERY  
RESTORE LOG adb FROM backup5 WITH NORECOVERY  
RESTORE LOG adb FROM tailLogBackup WITH RECOVERY  
```  
  
 復元しないファイルは、自動的にオンラインになります。 これで、すべてのファイル グループがオンラインになります。  
  
## 参照  
 [Online Restore &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [段階的な部分復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [ファイル復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  