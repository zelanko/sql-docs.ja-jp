---
title: sys.sp_xtp_unbind_db_resource_pool (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_xtp_unbind_db_resource_pool_TSQL
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool_TSQL
- sys.sp_xtp_unbind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool
ms.assetid: 695a796d-087e-4bc8-99d0-ddc342604c75
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 852d8db43c417d828678929f46ee28f12623a4af
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979414"
---
# <a name="sysspxtpunbinddbresourcepool-transact-sql"></a>sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  このシステム ストアド プロシージャは、追跡の目的でデータベースとリソース プールの既存のバインドを削除します。[!INCLUDE[hek_2](../../includes/hek-2-md.md)]メモリ使用量。  指定したデータベースに現在バインドされたプールがない場合、成功が返されます。 データベースのバインドが解除されると、メモリ最適化オブジェクトのために以前割り当てられたメモリは以前のリソース プールに割り当てられたままです。 割り当てられたメモリを解放するには、データベースを再起動する必要があります。 データベースとリソース プールとのバインドが解除されると、バインドは DEFAULT リソース プールを使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'database_name'  
```  
  
## <a name="arguments"></a>引数  
 database_name  
 既存の名前[!INCLUDE[hek_2](../../includes/hek-2-md.md)]データベースを有効にします。  
  
#### <a name="parameters"></a>パラメーター  
  
## <a name="messages"></a>メッセージ  
 データベースが名前付きリソース プールにバインドされていた場合、このプロシージャは正常に終了します。 ただし、バインドの解除を有効にするにはデータベースを再起動する必要があります。  
 指定したデータベースに既存のバインドが存在しない場合、`sp_xtp_unbind_db_resource_pool` は正常に終了しますが、次のような情報メッセージが表示されます。  
  
```  
Msg 41374, Level 16, State 1, Procedure sp_xtp_unbind_db_resource_pool_internal, Line 140.  
Database 'Hekaton_DB' does not have a binding to a resource pool.  
  
```  
  
## <a name="example"></a>例  
 次のコードは、バインドされた[!INCLUDE[hek_2](../../includes/hek-2-md.md)] リソース プールからデータベース Hekaton_DB をバインド解除します。  Hekaton_DB が[!INCLUDE[hek_2](../../includes/hek-2-md.md)] リソース プールに現在バインドされていない場合、メッセージが表示されます。 バインドの解除を有効にするにはデータベースを再起動する必要があります。  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'Hekaton_DB'  
```  
  
## <a name="requirements"></a>要件  
  
-   指定されるデータベース`database_name`へのバインドがあります、[!INCLUDE[hek_2](../../includes/hek-2-md.md)]リソース プール。  
  
-   CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルを持つデータベースのリソース プールへのバインド](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)  
  
  
