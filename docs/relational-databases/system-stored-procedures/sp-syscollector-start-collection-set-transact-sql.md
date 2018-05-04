---
title: sp_syscollector_start_collection_set (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_syscollector_start_collection_set_TSQL
- sp_syscollector_start_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_start_collection_set
ms.assetid: d8357180-f51e-4681-99f9-0596fe2d2b53
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 844bee9d8bcbb2c9e889cd3f4e9633a42c4cdeee
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spsyscollectorstartcollectionset-transact-sql"></a>sp_syscollector_start_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクターが既に有効になっており、コレクション セットがまだ実行されていない場合、コレクション セットを開始します。 コレクターが有効でない場合は、実行して、コレクターを有効に[sp_syscollector_enable_collector](../../relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql.md)し、このストアド プロシージャを使用して、コレクション セットを開始します。  

  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_start_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@collection_set_id =** ] *collection_set_id*  
 コレクション セットの一意なローカル識別子を指定します。 *collection_set_id*は**int**で、既定値は NULL です。 *collection_set_id*場合、値が必要*名前*は NULL です。  
  
 [  **@name =** ] '*名前*'  
 コレクション セットの名前を指定します。 *名前*は**sysname**で、既定値は NULL です。 *名前*場合、値が必要*collection_set_id*は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syscollector_create_collection_set を msdb システム データベースのコンテキストで実行し、SQL Server エージェントを有効にする必要があります。  
  
 このプロシージャをスケジュールがないコレクション セットに対して実行すると、失敗します。 場合、コレクション セットが、スケジュール (コレクション モード設定されているために非キャッシュなど) を使用して、 [sp_syscollector_run_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql.md)ストアド プロシージャをコレクション セットを開始します。  
  
 このプロシージャは、コレクションを有効にし、指定されたコレクション セットのジョブをアップロードして、コレクション セットのコレクション モードがキャッシュ (0) に設定されている場合は、直ちにコレクション エージェント ジョブを開始します。 詳細については、次を参照してください。 [sp_syscollector_create_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md)です。  
  
 コレクション セットにコレクション アイテムが含まれていない場合、この操作には何も効果がありません。 警告としてエラー 14685 が返されます。  
  
## <a name="permissions"></a>権限  
 このプロシージャを実行するには、dc_operator 固定データベース ロールのメンバーシップが必要です。 コレクション セットにプロキシ アカウントがない場合は、sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、識別子を使用してコレクション セットを開始します。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>参照  
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [データ コレクション](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
