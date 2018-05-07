---
title: sys.fn_cdc_increment_lsn (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- fn_cdc_increment_lsn_TSQL
- sys.fn_cdc_increment_lsn_TSQL
- sys.fn_cdc_increment_lsn
- fn_cdc_increment_lsn
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_increment_lsn
- sys.fn_cdc_increment_lsn
ms.assetid: e53b6703-358b-4c9a-912a-8f7c7331069b
caps.latest.revision: 18
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9202afab2c6b0fca9c230a60b1448a3069232d58
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysfncdcincrementlsn-transact-sql"></a>sys.fn_cdc_increment_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された LSN の直後のログ シーケンス番号 (LSN) を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_cdc_increment_lsn ( lsn_value )  
```  
  
## <a name="arguments"></a>引数  
 *lsn_value*  
 LSN 値を指定します。 *lsn_value*は**binary (10)** です。  
  
## <a name="return-type"></a>戻り値の型  
 **binary(10)**  
  
## <a name="remarks"></a>解説  
 この関数から返される LSN 値は、指定された値よりも必ず大きくなり、2 つの値の間に LSN 値は存在しません。  
  
 変更データを時間経過に沿って体系的にクエリするには、取得する変更の範囲を毎回変えながら、クエリ関数を定期的に呼び出す必要があります。 データの取得漏れを確実に防ぐ手段としては、前回のクエリの上限を基にして、後続のクエリの下限を決める方法がよく使用されます。 クエリ範囲は両端の値を含む閉区間となるため、新しい下限は、前回の上限よりも必ず大きく、かつ、新しい下限と前回の上限との間に、別の LSN 値を持った変更が入り込む余地のない程度に十分小さい値であることが必要です。 sys.fn_cdc_increment_lsn 関数は、このような値を取得するために使用します。  
  
## <a name="permissions"></a>権限  
 public データベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、前回のクエリ時に保存した上限を `sys.fn_cdc_increment_lsn` 変数に格納し、それを `@save_to_lsn` 関数に渡すことによって、変更データ キャプチャ クエリに使用する新しい下限値を取得しています。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10), @save_to_lsn binary(10);  
SET @save_to_lsn = <previous_upper_bound_value>;  
SET @from_lsn = sys.fn_cdc_increment_lsn(@save_to_lsn);  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SELECT * from cdc.fn_cdc_get_all_changes_HumanResources_Employee( @from_lsn, @to_lsn, 'all' );  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fn_cdc_decrement_lsn &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-decrement-lsn-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)   
 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [変更データ キャプチャについて &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
