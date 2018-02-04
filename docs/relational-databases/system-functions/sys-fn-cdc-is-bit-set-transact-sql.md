---
title: "sys.fn_cdc_is_bit_set (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- fn_cdc_is_bit_set
- sys.fn_cdc_is_bit_set_TSQL
- sys.fn_cdc_is_bit_set
- fn_cdc_is_bit_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_cdc_is_bit_set
- fn_cdc_is_bit_set
ms.assetid: 792fe7cf-b3b8-4f25-8329-78d63f0e6921
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 920a853813cce683d42fb319e5eae7043300c5f0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysfncdcisbitset-transact-sql"></a>sys.fn_cdc_is_bit_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  序数位置が指定されたビットマスク内にあるかどうかを確認することで、キャプチャした列が更新されているかどうかを示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_cdc_is_bit_set ( position , update_mask )  
```  
  
## <a name="arguments"></a>引数  
 *position*  
 確認するマスク内の序数位置を指定します。 *位置*は**int**です。  
  
 *update_mask*  
 更新された列を識別するマスクを指定します。 *update_mask* is **varbinary(128)**.  
  
## <a name="return-type"></a>戻り値の型  
 **bit**  
  
## <a name="remarks"></a>解説  
 通常、この関数は、列が変更されたかどうかを示すために変更データ クエリの一部として使用します。 このシナリオでは、関数で[sys.fn_cdc_get_column_ordinal](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md)クエリの前に必要な列の序数を取得するために使用します。 **sys.fn_cdc_is_bit_set**は返された結果セットの一部として列に固有の情報を提供する、返される変更データの各行に適用されます。  
  
 関数の代わりにこの関数を使用することをお勧め[sys.fn_cdc_has_column_changed](../../relational-databases/system-functions/sys-fn-cdc-has-column-changed-transact-sql.md)返された結果セットのすべての行の列が変更されたかどうかを判断する場合。  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`sys.fn_cdc_is_bit_set` を使用して、クエリ関数 `cdc.fn_cdc_get_all_changes_HR_Department` によって生成された結果セットの前に列 '`IsGroupNmUpdated`' を付加します。このとき、事前計算済みの列序数と `__$update_mask` の値を呼び出しの引数として使用しています。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10), @GroupNm_ordinal int;  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HR_Department');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SET @GroupNm_ordinal = sys.fn_cdc_get_column_ordinal('HR_Department','GroupName');  
  
SELECT sys.fn_cdc_is_bit_set(@GroupNm_ordinal,__$update_mask) as 'IsGroupNmUpdated', *  
FROM cdc.fn_cdc_get_all_changes_HR_Department( @from_lsn, @to_lsn, 'all')  
WHERE __$operation = 4;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [変更データ キャプチャの関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)   
 [sys.fn_cdc_get_column_ordinal &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-cdc-get-column-ordinal-transact-sql.md)   
 [sys.fn_cdc_has_column_changed &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-cdc-has-column-changed-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
