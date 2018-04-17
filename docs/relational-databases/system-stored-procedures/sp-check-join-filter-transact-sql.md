---
title: sp_check_join_filter (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- filter_TSQL
- sp_check_TSQL
- sp_check_join_filter
- sp_check_join_filter_TSQL
- join
- join_TSQL
- filter
- sp_check
helpviewer_keywords:
- sp_check_join_filter
ms.assetid: e9699d59-c8c9-45f6-a561-f7f95084a540
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6fb8f08e4b52debeba4e71011750733a2c760df1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spcheckjoinfilter-transact-sql"></a>sp_check_join_filter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  2 つのテーブル間の結合フィルターを検証し、結合フィルター句が有効かどうかを判別する場合に使用します。 このストアド プロシージャは、指定したテーブルの事前計算されたパーティションで、指定した結合フィルターを使用できるかどうかなど、指定した結合フィルターに関する情報を返します。 このストアド プロシージャは、パブリケーション上のパブリッシャー側で実行されます。 詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_check_join_filter [ @filtered_table = ] 'filtered_table'  
        , [@join_table = ] 'join_table'  
        , [ @join_filterclause = ] 'join_filterclause'  
```  
  
## <a name="arguments"></a>引数  
 [ **@filtered_table**=] **'***filtered_table***'**  
 フィルター済みテーブルの名前を指定します。 *filtered_table*は**nvarchar (400)**、既定値はありません。  
  
 [ **@join_table**=] **'***join_table***'**  
 結合するテーブルの名前を指定*filtered_table*です。 *join_table*は**nvarchar (400)**、既定値はありません。  
  
 [ **@join_filterclause** =] **'***join_filterclause***'**  
 テストする結合フィルター句を指定します。 *join_filterclause*は**nvarchar (1000)**、既定値はありません。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|パブリケーションが事前計算済みパーティションです。 適用されるかどうかは、します。ここで**1**示しパーティションを使用できることを意味し、 **0**使用できないことを意味します。|  
|**has_dynamic_filters**|**bit**|指定されたフィルター句に少なくとも 1 つのパラメーター化されたフィルター関数が含まれるかどうかは、します。ここで**1**パラメーター化されたフィルター関数を使用することを意味し、 **0**ような関数が使用されないことを意味します。|  
|**dynamic_filters_function_list**|**nvarchar(500)**|アーティクルのパラメーター化されたフィルターを定義する、フィルター句内の関数の一覧。各関数はセミコロンで区切られます。|  
|**uses_host_name**|**bit**|場合、 [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md)フィルター句で使用される関数を**1**この関数が存在することを意味します。|  
|**uses_suser_sname**|**bit**|場合、 [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md)フィルター句で使用される関数を**1**この関数が存在することを意味します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_check_join_filter**はマージ レプリケーションで使用します。  
  
 **sp_check_join_filter**公開されない場合でも、関連するテーブルに対して実行することができます。 このストアド プロシージャは、2 つのアーティクル間の結合フィルターを定義する前に、結合フィルター句を検証するときに使用できます。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_check_join_filter**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
