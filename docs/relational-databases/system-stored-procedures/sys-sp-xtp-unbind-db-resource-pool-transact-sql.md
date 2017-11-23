---
title: "sys.sp_xtp_unbind_db_resource_pool (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_xtp_unbind_db_resource_pool_TSQL
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool_TSQL
- sys.sp_xtp_unbind_db_resource_pool
dev_langs: TSQL
helpviewer_keywords:
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool
ms.assetid: 695a796d-087e-4bc8-99d0-ddc342604c75
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6da5bc97801329871d6b433ecf8f049f4b0eb742
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysspxtpunbinddbresourcepool-transact-sql"></a>sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  このシステム ストアド プロシージャは、追跡の目的でデータベースとリソース プールとの既存のバインドを削除[!INCLUDE[hek_2](../../includes/hek-2-md.md)]メモリ使用量。  指定したデータベースに現在バインドされたプールがない場合、成功が返されます。 データベースのバインドが解除されると、メモリ最適化オブジェクトのために以前割り当てられたメモリは以前のリソース プールに割り当てられたままです。 割り当てられたメモリを解放するには、データベースを再起動する必要があります。 データベースとリソース プールとのバインドが解除されると、バインドは DEFAULT リソース プールを使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
## <a name="syntax"></a>構文  
  
```tsql  
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
  
```tsql  
sys.sp_xtp_unbind_db_resource_pool 'Hekaton_DB'  
```  
  
## <a name="requirements"></a>必要条件  
  
-   指定されたデータベース`database_name`へのバインドが必要な[!INCLUDE[hek_2](../../includes/hek-2-md.md)]リソース プールです。  
  
-   CONTROL SERVER 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化テーブルを持つデータベースのリソース プールへのバインド](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)  
  
  
