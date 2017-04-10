---
title: "単純復旧モデルでのデータベース バックアップの復元 (Transact-SQL) | Microsoft Docs"
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
  - "完全バックアップ [SQL Server]"
  - "データベース復元 [SQL Server], 完全バックアップ"
  - "データベースのバックアップ [SQL Server]、完全バックアップ"
  - "データベース バックアップ [SQL Server]、完全バックアップ"
  - "データベースの復元 [SQL Server], 完全バックアップ"
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
caps.latest.revision: 39
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 39
---
# 単純復旧モデルでのデータベース バックアップの復元 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、データベースの完全バックアップを復元する方法について説明します。  
  
> [!IMPORTANT]  
>  データベースの完全バックアップの復元中は、復元作業を実行するシステム管理者以外は、復元中のデータベースを使用しないでください。  
  
## 前提条件と推奨事項  
  
-   暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。 証明書または非対称キーがないと、データベースは復元できません。 このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。 詳細については、「 [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)」を参照してください。  
  
-   セキュリティを確保するため、不明なソースや信頼されていないソースからのデータベースは、アタッチまたは復元しないことをお勧めします。 こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。 不明または信頼できないソースのデータベースを使用する前に、実稼働用ではないサーバーでそのデータベースに対し [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) を実行し、さらに、そのデータベースのストアド プロシージャやその他のユーザー定義コードなどのコードを調べます。  
  
## アップグレード後のデータベース互換性レベル  
 **tempdb**、**model**、**msdb**、および **Resource** データベースの互換性レベルは、アップグレード後に [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の互換性レベルに設定されます。 **master** システム データベースは、互換性レベルが 100 を下回っている場合を除いて、アップグレード前の互換性レベルを保持します。 アップグレード前の **master** の互換性レベルが 100 を下回っている場合は、アップグレード後、100 に設定されます。  
  
 アップグレード前のユーザー データベースの互換性レベルが 100 以上の場合は、アップグレード後も互換性レベルは変わりません。 アップグレード前の互換性レベルが 90 の場合、アップグレードされたデータベースの互換性レベルは 100 に設定されます。これは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でサポートされている下限の互換性レベルです。  
  
> [!NOTE]  
>  新しいユーザー データベースには、**model** データベースの互換性レベルが継承されます。  
  
## 手順  
  
#### データベースの完全バックアップを復元するには  
  
1.  次の項目を指定した RESTORE DATABASE ステートメントを実行し、データベースの完全バックアップを復元します。  
  
    -   復元するデータベースの名前。  
  
    -   データベースの完全バックアップの復元元バックアップ デバイス。  
  
    -   NORECOVERY 句。データベースの完全バックアップを復元した後に適用するトランザクション ログまたはデータベースの差分バックアップがある場合に指定します。  
  
    > [!IMPORTANT]  
    >  暗号化されたデータベースを復元するには、データベースの暗号化に使用された証明書または非対称キーにアクセスできることが必要です。 証明書または非対称キーがないと、データベースは復元できません。 このため、バックアップが必要である間は、データベース暗号化キーの暗号化に使用する証明書を保持しておく必要があります。 詳細については、「 [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)」を参照してください。  
  
2.  必要に応じて、以下も指定します。  
  
    -   FILE 句。バックアップ デバイス上の復元するバックアップ セットを識別するとき指定します。  
  
> [!NOTE]  
>  以前のバージョンのデータベースを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に復元すると、データベースが自動的にアップグレードされます。 通常、データベースは直ちに使用可能になります。 ただし、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] データベースにフルテキスト インデックスがある場合、アップグレード プロセスでは、**upgrade_option** サーバー プロパティの設定に応じて、インポート、リセット、または再構築が行われます。 アップグレード オプションがインポート (**upgrade_option** = 2) または再構築 (**upgrade_option** = 0) に設定されている場合、アップグレード中はフルテキスト インデックスを使用できなくなります。 インデックスを作成するデータ量によって、インポートには数時間、再構築には最大でその 10 倍の時間がかかることがあります。 また、アップグレード オプションがインポートに設定されており、フルテキスト カタログが使用できない場合は、関連付けられたフルテキスト インデックスが再構築されます。 **upgrade_option** サーバー プロパティの設定を変更するには、[sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md) を使用します。  
  
## 例  
  
### 説明  
 この例では、テープから [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] の完全データベース バックアップを復元します。  
  
### 例  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## 参照  
 [データベースの全体復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [データベースの全体復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [データベースの完全バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-database-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [バックアップの履歴とヘッダーの情報 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [システム データベースの再構築](../../relational-databases/databases/rebuild-system-databases.md)  
  
  