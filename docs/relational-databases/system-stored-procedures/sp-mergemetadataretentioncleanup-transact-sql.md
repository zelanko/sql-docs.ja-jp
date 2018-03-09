---
title: "sp_mergemetadataretentioncleanup (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_mergemetadataretentioncleanup
- sp_mergemetadataretentioncleanup_TSQL
helpviewer_keywords:
- sp_mergemetadataretentioncleanup
ms.assetid: 4e8d6343-2a38-421d-a3f3-c37d437a0f88
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f5ddc3ccb31599685dc9b41e383f29422b8b74e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spmergemetadataretentioncleanup-transact-sql"></a>sp_mergemetadataretentioncleanup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内のメタデータの手動クリーンアップを実行、 [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)、 [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)、 [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)、 [MSmerge_past_partition_マッピング](../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)、および[MSmerge_current_partition_mappings](../../relational-databases/system-tables/msmerge-current-partition-mappings.md)システム テーブル。 このストアド プロシージャは、トポロジ内の各パブリッシャーおよびサブスクライバーで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_mergemetadataretentioncleanup [ [ @num_genhistory_rows = ] num_genhistory_rows OUTPUT ]  
    [ , [ @num_contents_rows = ] num_contents_rows OUTPUT ]   
    [ , [ @num_tombstone_rows = ] num_tombstone_rows OUTPUT ]   
    [ , [ @aggressive_cleanup_only = ] aggressive_cleanup_only ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@num_genhistory_rows=** ] *num_genhistory_rows*出力  
 クリーンアップの行の数を返します、 [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)テーブル。 *num_genhistory_rows*は**int**、既定値は**0**します。  
  
 [  **@num_contents_rows=** ] *num_contents_rows*出力  
 クリーンアップの行の数を返します、 [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)テーブル。 *num_contents_rows*は**int**、既定値は**0**します。  
  
 [  **@num_tombstone_rows=** ] *num_tombstone_rows*出力  
 クリーンアップの行の数を返します、 [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)テーブル。 *num_tombstone_rows*は**int**、既定値は**0**します。  
  
 [  **@aggressive_cleanup_only=** ] *aggressive_cleanup_only*  
 内部使用のみです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  実行している場合は、データベースでの複数のパブリケーションが存在し、それらのパブリケーションのいずれかが無期限のパブリケーション保有期間を使用して、 **sp_mergemetadataretentioncleanup**クリーンアップ、マージ レプリケーション変更の追跡がありませんデータベースのメタデータ。 このため、無期限のパブリケーション保有期間は注意して使用してください。 かどうか、パブリケーションに無期限の保有期間を特定するのには、実行[sp_helpmergepublication (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md) 、パブリッシャーと注意結果内のすべてのパブリケーションの設定の値を持つ**0**の**保有**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **db_owner** 、パブリッシュされたデータベースが実行できるは、データベース ロールまたはパブリケーション アクセス リスト内のユーザーを固定**sp_mergemetadataretentioncleanup**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
