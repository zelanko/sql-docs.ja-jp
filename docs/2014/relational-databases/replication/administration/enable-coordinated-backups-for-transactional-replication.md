---
title: トランザクションレプリケーションの連携バックアップを有効にする (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- transactional replication, backup and restore
- sp_replicationdboption
- sync with backup [SQL Server replication]
- coordinated backups [SQL Server replication]
- backups [SQL Server replication], transactional replication
ms.assetid: 73a914ba-8b2d-4f4d-ac1b-db9bac676a30
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 77405cd968fa917c3ccc799eb7d168782443eee9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060800"
---
# <a name="enable-coordinated-backups-for-transactional-replication-replication-transact-sql-programming"></a>トランザクション レプリケーションの連携バックアップの有効化 (レプリケーション Transact-SQL プログラミング)
  データベースでトランザクション レプリケーションを有効にする場合、ディストリビューション データベースに配布する前にすべてのトランザクションをバックアップするように指定できます。 また、ディストリビューション データベースの連携バックアップを有効にして、ディストリビューターに反映されたトランザクションがバックアップされるまで、パブリケーション データベースのトランザクション ログが切り捨てられないようにすることができます。 詳細については、「 [スナップショット レプリケーションおよびトランザクション レプリケーションのバックアップと復元の方式](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)」を参照してください。  
  
### <a name="to-enable-coordinated-backups-for-a-database-published-with-transactional-replication"></a>トランザクション レプリケーションでパブリッシュされたデータベースの連携バックアップを有効にするには  
  
1.  パブリッシャーで、[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 関数を使用すると、パブリケーション データベースの **IsSyncWithBackup** プロパティが返されます。 この関数が **1**を返した場合、連携バックアップはパブリッシュされたデータベースに対して既に有効になっています。  
  
2.  手順 1. の関数が **0** を返した場合、パブリッシャー側のパブリケーション データベースに対して [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。 ** \@ Optname**に**sync with backup**を指定し、 ** \@ 値**に**true**を指定します。  
  
    > [!NOTE]  
    >  **sync with backup** オプションを **false**に変更すると、ログ リーダー エージェントが実行された後で、または一定の間隔で (ログ リーダー エージェントが継続的に実行されている場合)、パブリケーション データベースの切り捨てのポイントが更新されます。 最長間隔は、**-MessageInterval** エージェント パラメーター (既定値は 30 秒) によって制御されます。  
  
### <a name="to-enable-coordinated-backups-for-a-distribution-database"></a>ディストリビューション データベースの連携バックアップを有効にするには  
  
1.  ディストリビューターで、[DATABASEPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/databasepropertyex-transact-sql) 関数を使用すると、ディストリビューション データベースの **IsSyncWithBackup** プロパティが返されます。 この関数が **1**を返した場合、ディストリビューション データベースの連携バックアップは既に有効になっています。  
  
2.  手順 1. の関数が **0** を返した場合、ディストリビューター側のディストリビューション データベースに対して [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。 ** \@ Optname**に**sync with backup**を指定し、 ** \@ 値**に**true**を指定します。  
  
### <a name="to-disable-coordinated-backups"></a>連携バックアップを無効にするには  
  
1.  パブリッシャーのパブリケーション データベースで、またはディストリビューターのディストリビューション データベースで、[sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) を実行します。 ** \@ Optname**に**sync with backup**を指定し、 ** \@ 値**に**false**を指定します。  
  
  
