---
title: "sp_syscollector_stop_collection_set (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_stop_collection_set_TSQL
- sp_syscollector_stop_collection_set
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_stop_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 4668cfb7-462f-40d0-948c-8f740a792a4d
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0d98b748e4b733ae9c56319e83f8d9a12a62e4a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectorstopcollectionset-transact-sql"></a>sp_syscollector_stop_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクション セットを停止します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_stop_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @stop_collection_job = ] stop_collection_job ]  
```  
  
## <a name="arguments"></a>引数  
 [ @collection_set_id =] *collection_set_id*  
 コレクション セットの一意なローカル識別子を指定します。 *collection_set_id*は**int**で、既定値は NULL です。 *collection_set_id*場合、値が必要*名前*は NULL です。  
  
 [ @name =] '*名前*'  
 コレクション セットの名前を指定します。 *名前*は**sysname**で、既定値は NULL です。 *名前*場合、値が必要*collection_set_id*は NULL です。  
  
 [ @stop_collection_job =] *stop_collection_job*  
 コレクション セットのコレクション ジョブが実行されている場合に、停止を指定します。 *stop_collection_job*は**ビット**既定値は 1 です。  
  
 *stop_collection_job*コレクション モードを設定してキャッシュにコレクション セットにのみ適用されます。 詳細については、次を参照してください。 [sp_syscollector_create_collection_set (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_syscollector_create_collection_set は、msdb システム データベースのコンテキストで実行する必要があります。  
  
## <a name="permissions"></a>Permissions  
 このプロシージャを実行するには、(EXECUTE 権限を持つ) dc_operator 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、識別子を使用してコレクション セットを停止します。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>参照  
 [データ コレクション](../../relational-databases/data-collection/data-collection.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
