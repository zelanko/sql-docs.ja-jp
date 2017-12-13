---
title: "sp_replcounters (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_replcounters
- sp_replcounters_TSQL
helpviewer_keywords: sp_replcounters
ms.assetid: fe585b1f-edda-421f-81d6-8a03a3a535d2
caps.latest.revision: "24"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 64ce16cd3b23c1c0bf0526619f90c7028ff80df6
ms.sourcegitcommit: 0431de135547f5aff48d6cad57090717f27bc063
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="spreplcounters-transact-sql"></a>sp_replcounters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブッリッシュされたデータベースごとに、待機時間、スループット、トランザクション数に関するレプリケーションの統計を返します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replcounters  
  
```  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**データベース**|**sysname**|データベースの名前です。|  
|**レプリケートされたトランザクション**|**int**|ディストリビューション データベースへの配信を待機する、ログ内のトランザクション数。|  
|**レプリケーション率トランザクション/秒**|**float**|ディストリビューション データベースに配信された 1 秒あたりの平均トランザクション数。|  
|**レプリケーションの待機時間**|**float**|配信されるまでにトランザクションがログに格納されていた平均秒数。|  
|**Replbeginlsn**|**binary(10)**|ログにおける、現在の切り捨てポイントのログ シーケンス番号 (LSN)。|  
|**Replnextlsn**|**binary(10)**|ディストリビューション データベースへの配信を待機する、次のコミット レコードの LSN。|  
  
## <a name="remarks"></a>解説  
 **sp_replcounters**トランザクション レプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **db_owner**固定データベース ロールまたは**sysadmin**固定サーバー ロール。  
  
## <a name="see-also"></a>参照  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
