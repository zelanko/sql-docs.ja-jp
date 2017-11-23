---
title: "sys.fn_cdc_get_max_lsn (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
f1_keywords:
- sys.fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn
- fn_cdc_get_max_lsn_TSQL
- sys.fn_cdc_get_max_lsn_TSQL
dev_langs: TSQL
helpviewer_keywords:
- fn_cdc_get_max_lsn
- sys.fn_cdc_get_max_lsn
ms.assetid: 93f3a4c8-b91f-4ebb-8e96-9397bb3a1c43
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 879aabe94705b78433188ff821c760937d2c9511
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysfncdcgetmaxlsn-transact-sql"></a>sys.fn_cdc_get_max_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内の start_lsn 列から最大ログ シーケンス番号 (LSN) を返します、 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)システム テーブル。 この関数を使用すると、任意のキャプチャ インスタンスについて、変更データ キャプチャ タイムラインの上端を取得できます。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_cdc_get_max_lsn ()  
```  
  
## <a name="return-types"></a>戻り値の型  
 **binary(10)**  
  
## <a name="remarks"></a>解説  
 この関数では、最大の LSN を返しますの start_lsn 列で、 [cdc.lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)テーブル。 変更がデータベース変更テーブルに反映されたときに、キャプチャ プロセスで最後に処理された LSN になります。 これは、データベースに対して定義されているキャプチャ インスタンスに関連付けられたすべてのタイムラインの上端として使用されます。  
  
 通常は、関数を使用してクエリ範囲に対する適切な上端を取得します。  
  
## <a name="permissions"></a>Permissions  
 public データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-maximum-lsn-value"></a>A. 最大 LSN 値を取得する  
 次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内のすべてのキャプチャ インスタンスの最大 LSN を返します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT sys.fn_cdc_get_max_lsn()AS max_lsn;  
```  
  
### <a name="b-setting-the-high-endpoint-of-a-query-range"></a>B. クエリ範囲の上端を設定する  
 次の例では、`sys.fn_cdc_get_max_lsn` によって返された最大 LSN を使用して、キャプチャ インスタンス `HumanResources_Employee` に対するクエリ範囲の上端を設定します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn(N'HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fn_cdc_get_min_lsn &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)  
  
  
