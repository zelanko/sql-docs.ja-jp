---
title: "sys.sp_cdc_get_captured_columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns_TSQL
- sp_cdc_get_captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_get_captured_columns
- sp_cdc_get_captured_columns
- change data capture [SQL Server], querying metadata
ms.assetid: d9e680be-ab9b-4e0c-b63a-90658f241df8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e232446f85dabc19856913ebf2e0cc5f886dc8cb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdcgetcapturedcolumns-transact-sql"></a>sys.sp_cdc_get_captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したキャプチャ インスタンスによって追跡されるキャプチャ対象のソース列について、変更データ キャプチャのメタデータ情報を返します。 変更データ キャプチャは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_get_captured_columns   
    [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>引数  
 [ @capture_instance =] '*capture_instance*'  
 ソース テーブルに関連付けられたキャプチャ インスタンスの名前を指定します。 *capture_instance*は**sysname** NULL にすることはできません。  
  
 報告するために、テーブルのキャプチャ インスタンスの実行、 [sys.sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)ストアド プロシージャです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|ソース テーブルのスキーマ名です。|  
|source_table|**sysname**|ソース テーブルの名前です。|  
|capture_instance|**sysname**|キャプチャ インスタンスの名前です。|  
|column_name|**sysname**|キャプチャ対象のソース列の名前です。|  
|column_id|**int**|ソース テーブル内の列の ID です。|  
|ordinal_position|**int**|ソース テーブル内での列の位置です。|  
|data_type|**sysname**|列のデータ型です。|  
|character_maximum_length|**int**|文字ベースの列の場合は最大文字長です。それ以外の場合は、NULL です。|  
|numeric_precision|**tinyint**|数値ベースの場合は、列の有効桁数です。それ以外の場合は、NULL です。|  
|numeric_precision_radix|**smallint**|数値ベースの場合は、列の有効桁数の基数です。それ以外の場合は、NULL です。|  
|numeric_scale|**int**|数値ベースの場合は、列の小数点以下桁数です。それ以外の場合は、NULL です。|  
|datetime_precision|**smallint**|datetime ベースの場合は、列の有効桁数です。それ以外の場合は NULL です。|  
  
## <a name="remarks"></a>解説  
 Sys.sp_cdc_get_captured_columns を使用して、キャプチャ インスタンスのクエリ関数によって返されたキャプチャ対象列の列情報を取得する[cdc.fn_cdc_get_all_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)または[cdc.fn_cdc_get_net_changes_ < capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)です。 列名、ID、および位置は、キャプチャ インスタンスの有効期間中は常に一定です。 追跡対象テーブルの基になるソース列のデータ型が変更された場合にのみ、列のデータ型が変化します。 追加またはソース テーブルから削除されている列は、既存のキャプチャ インスタンスのキャプチャ対象列に対する影響を与えるありません。  
  
 使用して[sys.sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md)情報を取得するデータ定義言語 (DDL) ステートメントのソース テーブルに適用します。 DDL の変更によって追跡対象ソース列の構造が変更された場合、そのような DDL の変更がすべて結果セットとして返されます。  
  
## <a name="permissions"></a>Permissions  
 db_owner 固定データベース ロールのメンバーシップが必要です。 それ以外のすべてのユーザーについては、ソース テーブルのすべてのキャプチャ対象列に対する SELECT 権限が必要です。さらに、キャプチャ インスタンスのゲーティング ロールが定義されている場合は、そのデータベース ロールのメンバーシップが必要です。 呼び出し元にソース データを表示する権限がない場合、エラー 22981 (オブジェクトが存在しないか、アクセスが拒否されました。) が返されます。  
  
## <a name="examples"></a>使用例  
 次の例は、`HumanResources_Employee` キャプチャ インスタンスに存在するキャプチャ対象列の情報を返します。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_get_captured_columns   
    @capture_instance = N'HumanResources_Employee';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_help_change_data_capture &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
