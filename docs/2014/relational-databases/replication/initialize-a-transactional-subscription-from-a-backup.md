---
title: バックアップからのトランザクションサブスクリプションの初期化 (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: d0637fc4-27cc-4046-98ea-dc86b7a3bd75
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1563d58f2d54f77680781e22a162112ade1658e4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057108"
---
# <a name="initialize-a-transactional-subscription-from-a-backup-replication-transact-sql-programming"></a>トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)
  トランザクション パブリケーションのサブスクリプションは通常、スナップショットを使用して初期化されますが、レプリケーション ストアド プロシージャを使用して、バックアップからサブスクリプションを初期化することもできます。 詳細については、「 [スナップショットを使用しないトランザクション サブスクリプションの初期化](initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。  
  
### <a name="to-initialize-a-transactional-subscriber-from-a-backup"></a>トランザクション サブスクライバーをバックアップから初期化するには  
  
1.  既存のパブリケーションの場合は、パブリッシャーのパブリケーション データベースで [sp_helppublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) を実行して、バックアップから初期化する機能をパブリケーションがサポートしているかどうかを確認します。 結果セットの **allow_initialize_from_backup** の値を確認します。  
  
    -   この値が **1**の場合、パブリケーションはこの機能をサポートしています。  
  
    -   この値が **0** の場合、パブリッシャー側のパブリケーション データベースに対して [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql) を実行します。 値には、 ** \@ プロパティ**に**allow_initialize_from_backup**を指定し、値にはを指定し `true` ます** \@ **。  
  
2.  新しいパブリケーションの場合、パブリッシャー側のパブリケーション データベースに対して [sp_addpublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) を実行します。 Allow_initialize_from_backup には、の値を指定し `true` ます。 **allow_initialize_from_backup** 詳細については、「 [Create a Publication](publish/create-a-publication.md)」を参照してください。  
  
    > [!WARNING]  
    >  サブスクライバー データの欠落を回避するために、 **sp_addpublication** で `@allow_initialize_from_backup = N'true'`を使用する場合は、常に `@immediate_sync = N'true'`を使用します。  
  
3.  [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) ステートメントを使用して、パブリケーション データベースのバックアップを作成します。  
  
4.  [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) ステートメントを使用し、サブスクライバー上でバックアップを復元します。  
  
5.  パブリッシャー側のパブリケーション データベースに対して、ストアド プロシージャ [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) を実行します。 次のパラメーターを指定します。  
  
    -   ** \@ sync_type** - **backup を使用した初期化**の値。  
  
    -   ** \@ backupdevicetype** -バックアップデバイスの種類 (**論理**(既定)、**ディスク**、または**テープ**)。  
  
    -   ** \@ backupdevicename** -復元に使用する論理バックアップデバイスまたは物理バックアップデバイス。  
  
         論理デバイスの場合は、 **sp_addumpdevice** を使ってデバイスを作成する際に指定したバックアップ デバイスの名前を指定します。  
  
         物理デバイスの場合は、「 `DISK = 'C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\BACKUP\Mybackup.dat'` 」または「 `TAPE = '\\.\TAPE0'`」のように、完全なパスとファイル名を指定します。  
  
    -   Optional** \@ パスワード**-バックアップセットの作成時に指定されたパスワード。  
  
    -   Optional** \@ mediapassword** -メディアセットのフォーマット時に指定されたパスワード。  
  
    -   Optional** \@ fileidhint** -復元するバックアップセットの識別子。 たとえば、 **1** はバックアップ メディアの 1 番目のバックアップ セットを示し、 **2** は 2 番目のバックアップ セットを示します。  
  
    -   (テープデバイスの場合は省略可能)** \@ unload** -復元が完了した後にテープをドライブからアンロードする場合は**1** (既定値) を、アンロードしない場合は**0**を指定します。  
  
6.  (省略可能) プル サブスクリプションの場合は、サブスクライバーのサブスクリプション データベースで [sp_addpullsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql) と [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql) を実行します。 詳細については、「 [プル サブスクリプションの作成](create-a-pull-subscription.md)」をご覧ください。  
  
7.  (省略可) ディストリビューション エージェントを起動します。 詳細については、「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md) 」または「 [Synchronize a Push Subscription](synchronize-a-push-subscription.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [バックアップと復元によるデータベースのコピー](../databases/copy-databases-with-backup-and-restore.md)   
 [SQL Server データベースのバックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
  
