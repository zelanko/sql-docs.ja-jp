---
title: "トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/29/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "manual subscription initialization [SQL Server replication]"
  - "subscriptions [SQL Server replication], initializing"
  - "サブスクリプションの初期化 [SQL Server レプリケーション], スナップショットなし"
  - "トランザクション レプリケーション, バックアップと復元"
  - "バックアップ [SQL Server レプリケーション], トランザクション レプリケーション"
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)
  トランザクション パブリケーションのサブスクリプションは通常、スナップショットを使用して初期化されますが、レプリケーション ストアド プロシージャを使用して、バックアップからサブスクリプションを初期化することもできます。 詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)です。  
  
### トランザクション サブスクライバーをバックアップから初期化するには  
  
1.  既存のパブリケーションのパブリケーションが実行することによって、バックアップから初期化する機能をサポートしていることを確認して [sp_helppublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値に注意してください **allow_initialize_from_backup** 結果に設定します。  
  
    -   値の場合 **1**, 、パブリケーションは、この機能をサポートしています。  
  
    -   値の場合 **0**, 、実行 [sp_changepublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **allow_initialize_from_backup** の **@property** の **true** の **@value**します。  
  
2.  新規パブリケーションの場合は、次のように実行します。 [sp_addpublication & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **true** の **allow_initialize_from_backup**します。 詳しくは、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」をご覧ください。  
  
    > [!WARNING]  
    >  使用する場合、サブスクライバー データの欠落を回避する **sp_addpublication** と `@allow_initialize_from_backup = N'true'`, 、常に使用する `@immediate_sync = N'true'`です。  
  
3.  使用して、パブリケーション データベースのバックアップを作成、 [バックアップと #40 です。Transact SQL と #41;](../../t-sql/statements/backup-transact-sql.md) ステートメント。  
  
4.  使用してサブスクライバー上のバックアップの復元、 [復元と #40 です。Transact SQL と #41;](../Topic/RESTORE%20\(Transact-SQL\).md) ステートメント。  
  
5.  パブリッシャー側でパブリケーション データベースでストアド プロシージャを実行 [sp_addsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)です。 次のパラメーターを指定します。  
  
    -   **@sync_type** -値の **バックアップを使用して初期化**します。  
  
    -   **@backupdevicetype** -バックアップ デバイスの種類: **論理** (既定)、 **ディスク**, 、または **テープ**します。  
  
    -   **@backupdevicename** -復元操作に使用する論理または物理バックアップ デバイス。  
  
         論理デバイスの場合に指定されたバックアップ デバイスの名前を指定 **sp_addumpdevice** 、デバイスの作成に使用します。  
  
         物理デバイスの場合は、「`DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\BACKUP\Mybackup.dat'`」または「`TAPE = '\\.\TAPE0'`」のように、完全なパスとファイル名を指定します。  
  
    -   (省略可能) **@password** -バックアップ セットの作成時に指定されたパスワードです。  
  
    -   (省略可能) **@mediapassword** -メディア セットのフォーマット時に指定されたパスワードです。  
  
    -   (省略可能) **@fileidhint** -復元するバックアップ セットの識別子。 などを指定する **1** 最初のバックアップがバックアップ メディアのセットを示すと **2** 2 番目のバックアップ セットを指定します。  
  
    -   (テープ デバイスの省略可能) **@unload** -の値を指定して **1** (既定) 場合、復元が完了した後にテープがドライブからアンロードにするか、 **0** アンロードする必要がない場合。  
  
6.  (省略可能)プル サブスクリプションを実行する [sp_addpullsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)  [sp_addpullsubscription_agent & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) サブスクライバー側でサブスクリプション データベースです。 詳細については、「 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)」を参照してください。  
  
7.  (省略可) ディストリビューション エージェントを起動します。 詳細については、「 [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md) 」または「 [Synchronize a Push Subscription](../../relational-databases/replication/synchronize-a-push-subscription.md)」を参照してください。  
  
## 参照  
 [バックアップと復元によるデータベースのコピー](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  