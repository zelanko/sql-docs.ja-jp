---
title: sp_check_dynamic_filters (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- dynamic_filters_TSQL
- sp_check_TSQL
- check
- sp_check_dynamic filter
- check_TSQL
- filters_TSQL
- check_dynamic_filters_TSQL
- dynamic filters
- filters
- check dynamic filters
- sp_check_dynamic filter_TSQL
- sp_check_for_sync_trigger_TSQL
- sp_check
helpviewer_keywords:
- sp_check_dynamic_filters
ms.assetid: dd7760db-a3a5-460f-bd97-b8d436015e19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 979b61238b6d4f8faa39c90e116434426321273f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52811444"
---
# <a name="spcheckdynamicfilters-transact-sql"></a>sp_check_dynamic_filters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションについて、パラメーター化された行フィルターのプロパティに関する情報を表示します。特に、パブリケーション用にフィルター選択されたデータ パーティションを生成するための関数についての情報や、事前計算済みパーティションをパブリケーションで使用できるかどうかを示します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_check_dynamic_filters [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication**=] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|パブリケーションで事前計算済みパーティションを使用するためには場所**1**事前計算済みパーティションを使用できる、ことを意味し、 **0**が使用できないことを意味します。|  
|**has_dynamic_filters**|**bit**|少なくとも 1 つのパラメーター化された行フィルターがパブリケーションで定義されてかどうかは、します。場所**1**は 1 つまたは複数のパラメーター化された行フィルターが存在することを意味し、 **0**動的フィルターが存在しないことを意味します。|  
|**dynamic_filters_function_list**|**nvarchar(500)**|パブリケーション内にあるアーティクルをフィルター選択するための関数の一覧。各関数はセミコロン (;) で区切られます。|  
|**validate_subscriber_info**|**nvarchar(500)**|パブリケーション内にあるアーティクルをフィルター選択するための関数の一覧。各関数はプラス記号 (+) で区切られます。|  
|**uses_host_name**|**bit**|場合、 [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md)関数がパラメーター化された行フィルターで使用される、 **1**動的フィルター選択に対してこの関数を使用することを意味します。|  
|**uses_suser_sname**|**bit**|場合、 [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md)関数がパラメーター化された行フィルターで使用される、 **1**動的フィルター選択に対してこの関数を使用することを意味します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_check_dynamic_filters**はマージ レプリケーションで使用します。  
  
 パブリケーションが事前計算済みパーティションを使用する定義済みの場合**sp_check_dynamic_filters**事前計算済みパーティションの制限の違反を確認します。 違反が見つかった場合、エラーが返されます。 詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。  
  
 パブリケーションにパラメーター化された行フィルターがあることが定義されていても、パラメーター化された行フィルターが見つからない場合は、エラーが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_check_dynamic_filters**します。  
  
## <a name="see-also"></a>参照  
 [パラメーター化されたフィルターによるマージ パブリケーションのパーティションを管理します。](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [sp_check_join_filter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-join-filter-transact-sql.md)   
 [sp_check_subset_filter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-check-subset-filter-transact-sql.md)  
  
  
