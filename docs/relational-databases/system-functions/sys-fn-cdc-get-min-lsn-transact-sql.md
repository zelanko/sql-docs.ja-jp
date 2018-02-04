---
title: "sys.fn_cdc_get_min_lsn (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.fn_cdc_get_min_lsn
- fn_cdc_get_min_lsn
- fn_cdc_get_min_lsn_TSQL
- sys.fn_cdc_get_min_lsn_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_min_lsn
- sys.fn_cdc_get_min_lsn
ms.assetid: bd49e28a-128b-4f6b-8545-6a2ec3f4afb3
caps.latest.revision: 
author: BYHAM
ms.author: rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6d77250f4e595d121f89a112366dfbc9ee9600ad
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysfncdcgetminlsn-transact-sql"></a>sys.fn_cdc_get_min_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したキャプチャ インスタンスの start_lsn 列の値を返します、 [cdc.change_tables](../../relational-databases/system-tables/cdc-change-tables-transact-sql.md)システム テーブル。 この値は、キャプチャ インスタンスの有効期間の下端を表します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.fn_cdc_get_min_lsn ( 'capture_instance_name' )  
```  
  
## <a name="arguments"></a>引数  
 **'** *capture_instance_name* **'**  
 キャプチャ インスタンスの名前を指定します。 *capture_instance_name*は**sysname**です。  
  
## <a name="return-types"></a>戻り値の型  
 **binary(10)**  
  
## <a name="remarks"></a>解説  
 キャプチャ インスタンスが存在しない場合、または、キャプチャ インスタンスに関連付けられた変更データにアクセスするための権限が呼び出し元にない場合は、0x00000000000000000000 が返されます。  
  
 この関数の主な用途は、キャプチャ インスタンスに関連付けられた変更データ キャプチャ タイムラインの下端を識別することです。 変更データを要求する前に、クエリ範囲の両端がキャプチャ インスタンスのタイムライン内にあるかどうかを検証する場合にも、この関数を使用できます。 変更テーブルでクリーンアップが実行されると、キャプチャ インスタンスの下端が変わるため、こうしたチェックを実行することは重要です。 変更データを要求する間隔が開きすぎると、下端を前回の変更データ要求の上端に設定していたとしても、下端が現在のタイムラインから外れている可能性があります。  
  
## <a name="permissions"></a>権限  
 固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーシップが必要です。 それ以外のすべてのユーザーについては、ソース テーブルのすべてのキャプチャ対象列に対する SELECT 権限が必要です。さらに、キャプチャ インスタンスのゲーティング ロールが定義されている場合は、そのデータベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-the-minimum-lsn-value-for-a-specified-capture-instance"></a>A. 指定したキャプチャ インスタンスの最小 LSN 値を取得する  
 次の例は、キャプチャ インスタンスの最小 LSN 値を返します`HumanResources_Employee`で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
USE AdventureWorks2-12;  
GO  
SELECT sys.fn_cdc_get_min_lsn ('HumanResources_Employee')AS min_lsn;  
  
```  
  
### <a name="b-verifying-the-low-endpoint-of-a-query-range"></a>B. クエリ範囲の下端を検証する  
 次の例では、変更データ クエリの下端候補が、キャプチャ インスタンス `sys.fn_cdc_get_min_lsn` の現在のタイムラインに対して有効かどうかを、`HumanResources_Employee` によって返された最小 LSN 値を使って検証します。 この例では、前回の上端 LSN、キャプチャ インスタンスが保存されたおよび設定を利用できること、`@save_to_lsn`変数。 この例の目的で`@save_to_lsn`を実行するエラー処理セクションを強制的に 0x000000000000000000 に設定されています。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @min_lsn binary(10), @from_lsn binary(10),@save_to_lsn binary(10), @to_lsn binary(10);  
-- Sets @save_to_lsn to the previous high endpoint saved from the last change data request.  
SET @save_to_lsn = 0x000000000000000000;  
-- Sets the upper endpoint for the query range to the current maximum LSN.  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
-- Sets the @min_lsn parameter to the current minimum LSN for the capture instance.  
SET @min_lsn = sys.fn_cdc_get_min_lsn ('HumanResources_Employee');  
-- Sets the low endpoint for the query range to the LSN that follows the previous high endpoint.  
SET @from_lsn = sys.fn_cdc_increment_lsn(@save_to_lsn);  
-- Tests to verify the low endpoint is valid for the current capture instance.  
IF (@from_lsn < @min_lsn)  
    BEGIN  
        RAISERROR('Low endpoint of the request interval is invalid.', 16, -1);  
    END  
ELSE  
-- Return the changes occurring within the query range.  
    SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee(@from_lsn, @to_lsn, 'all');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.fn_cdc_get_max_lsn &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-cdc-get-max-lsn-transact-sql.md)   
 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)  
  
  
