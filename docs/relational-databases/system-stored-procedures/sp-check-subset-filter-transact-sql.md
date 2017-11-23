---
title: "sp_check_subset_filter (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_check_TSQL
- sp_check_subset_filter
- filter
- subset
- subset_TSQL
- sp_check
- sp_check_subset_filter_TSQL
helpviewer_keywords: sp_check_subset_filter
ms.assetid: 525cfcfc-f317-478d-ba84-72e62285f160
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3341c4f5fc6c637f74dabf913730e6c6e30dfcea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spchecksubsetfilter-transact-sql"></a>sp_check_subset_filter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テーブルに対してフィルター句を確認して、フィルター句がテーブルに対して有効であるかどうかを判定するのに使用します。 このストアド プロシージャは、フィルターが事前計算済みパーティションでの使用条件を満たすかどうかも含め、指定されたフィルターに関する情報を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーションを含むデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_check_subset_filter [ @filtered_table = ] 'filtered_table'  
        , [ @subset_filterclause = ] 'subset_filterclause'  
    [ , [ @has_dynamic_filters = ] has_dynamic_filters OUTPUT ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@filtered_table** =] **'***filtered_table***'**  
 フィルター済みテーブルの名前を指定します。 *filtered_table*は**nvarchar (400)**、既定値はありません。  
  
 [  **@subset_filterclause**  =] **'***subset_filterclause***'**  
 テストの対象となるフィルター句を指定します。 *subset_filterclause*は**nvarchar (1000)**、既定値はありません。  
  
 [  **@has_dynamic_filters** =] *has_dynamic_filters*  
 フィルター句がパラメーター化された行フィルターであるかどうかを示します。 *has_dynamic_filters*は**ビット**、既定値は NULL は出力パラメーターです。 値を返します**1**フィルター句がパラメーター化された行フィルターの場合。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**can_use_partition_groups**|**bit**|パブリケーションで事前計算済みパーティションを使用できるかどうかは、します。ここで**1**は事前計算済みパーティションを使用することができます、ことを意味し、 **0**使用できないことを意味します。|  
|**has_dynamic_filters**|**bit**|指定したフィルター句が; には、少なくとも 1 つのパラメーター化された行フィルターが含まれるかどうかは、します。ここで**1**パラメーター化された行フィルターを使用することを意味し、 **0**ような関数が使用されないことを意味します。|  
|**dynamic_filters_function_list**|**nvarchar (500)**|アーティクルを動的にフィルター選択するフィルター句内の関数の一覧です。各関数は、セミコロンで区切られます。|  
|**uses_host_name**|**bit**|場合、 [HOST_NAME()](../../t-sql/functions/host-name-transact-sql.md)フィルター句で使用される関数を**1**この関数が存在することを意味します。|  
|**uses_suser_sname**|**bit**|場合、 [SUSER_SNAME()](../../t-sql/functions/suser-sname-transact-sql.md)フィルター句で使用される関数を**1**この関数が存在することを意味します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_check_subset_filter**はマージ レプリケーションで使用します。  
  
 **sp_check_subset_filter**テーブルがパブリッシュされていない場合でも、任意のテーブルに対して実行することができます。 このストアド プロシージャを使用して、フィルター選択されたアーティクルを定義する前にフィルター句を検証することができます。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_check_subset_filter**です。  
  
## <a name="see-also"></a>参照  
 [事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンスを最適化します。](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)  
  
  
