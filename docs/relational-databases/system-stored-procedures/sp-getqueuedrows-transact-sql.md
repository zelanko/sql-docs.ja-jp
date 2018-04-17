---
title: sp_getqueuedrows (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_getqueuedrows_TSQL
- sp_getqueuedrows
helpviewer_keywords:
- sp_getqueuedrows
ms.assetid: 139e834f-1988-4b4d-ac81-db1f89ea90e8
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1915bec9f0a9f1e05bfe6a2975553bb20e330289
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spgetqueuedrows-transact-sql"></a>sp_getqueuedrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更新がキューに保留されているサブスクライバーで行を取得します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getqueuedrows [ @tablename = ] 'tablename'  
    [ , [ @owner = ] 'owner'  
    [ , [ @tranid = ] 'transaction_id' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@tablename =**] **'***tablename***'**  
 テーブルの名前を指定します。 *tablename*は**sysname**、既定値はありません。 テーブルは、キューに登録されているサブスクリプションの一部でなければなりません。  
  
 [  **@owner =**] **'***所有者***'**  
 サブスクリプションの所有者です。 *所有者*は**sysname**、既定値は NULL です。  
  
 [  **@tranid =** ] **'***transaction_id***'**  
 出力をトランザクション ID でフィルター選択できます。 *transaction_id*は**nvarchar (70)**、既定値は NULL です。 指定する場合、キューに登録されたコマンドに関連付けられているトランザクション ID が表示されます。 NULL の場合、キュー内のすべてのコマンドが表示されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 サブスクライブされたテーブルについて、現在、キューに少なくとも 1 つのトランザクションが登録されているすべての行を表示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**操作**|**nvarchar(10)**|同期を実行するときに行われるアクションの種類。<br /><br /> INS= 挿入<br /><br /> DEL = 削除<br /><br /> UPD = 更新|  
|**Tranid**|**nvarchar (70)**|コマンドが実行されたときのトランザクション ID。|  
|**テーブルの列 1... n**||指定されたテーブルの各列の値*tablename*です。|  
|**msrepl_tran_version**|**uniqueidentifier**|この列は、レプリケートされたデータの変更を追跡し、パブリッシャーで競合を検出するために使用されます。 またこの列は、自動的にテーブルに追加されます。|  
  
## <a name="remarks"></a>解説  
 **sp_getqueuedrows**キュー更新に参加しているサブスクライバーで使用します。  
  
 **sp_getqueuedrows**検索するデータベースのサブスクリプションで指定されたテーブルの行は、キュー更新に参加しているまだ現在解決されていないキュー リーダー エージェントによってです。  
  
## <a name="permissions"></a>権限  
 **sp_getqueuedrows**で指定されたテーブルに対する SELECT 権限が必要です*tablename*です。  
  
## <a name="see-also"></a>参照  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [キュー更新における競合の検出と解決](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
