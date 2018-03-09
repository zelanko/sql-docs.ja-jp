---
title: "sys.sp_cdc_get_ddl_history (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_cdc_get_ddl_history
- sp_cdc_get_ddl_history_TSQL
- sys.sp_cdc_get_ddl_history_TSQL
- sys.sp_cdc_get_ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], querying metadata
- sp_cdc_get_ddl_history
- sys.sp_cdc_get_ddl_history
ms.assetid: 4dee5e2e-d7e5-4fea-8037-a4c05c969b3a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 47c7d92dc4abcc05d056102e7020b61196aac068
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="sysspcdcgetddlhistory-transact-sql"></a>sys.sp_cdc_get_ddl_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたキャプチャ インスタンスに関連付けられたデータ定義言語 (DDL) の変更履歴を返します。変更履歴は、指定されたキャプチャ インスタンスに対して変更データ キャプチャが有効にされた時点からの履歴になります。 変更データ キャプチャは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_get_ddl_history [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>引数  
 [ @capture_instance =] '*capture_instance*'  
 ソース テーブルに関連付けられたキャプチャ インスタンスの名前を指定します。 *capture_instance*は**sysname** NULL にすることはできません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|ソース テーブルのスキーマ名です。|  
|source_table|**sysname**|ソース テーブルの名前です。|  
|capture_instance|**sysname**|キャプチャ インスタンスの名前です。|  
|required_column_update|**bit**|DDL の変更で、ソース列に対して行われたデータ型の変更を反映するために、変更テーブルの列を更新する必要があったことを示します。|  
|ddl_command|**nvarchar(max)**|ソース テーブルに適用された DDL ステートメントです。|  
|ddl_lsn|**binary(10)**|DDL の変更に関連付けられたログ シーケンス番号 (LSN) です。|  
|ddl_time|**datetime**|DDL の変更に関連付けられた時刻です。|  
  
## <a name="remarks"></a>解説  
 追加することや、列を削除または既存の列のデータ型の変更など、ソースのテーブルの列構造を変更する、ソース テーブルに対する DDL の変更が保持される、 [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md)テーブル。 このストアド プロシージャでは、こうした変更をレポートできます。 cdc.ddl_history のエントリは、キャプチャ プロセスで、ログから DDL トランザクションが読み取られた時点で作成されます。  
  
## <a name="permissions"></a>Permissions  
 データベースのすべてのキャプチャ インスタンスの行を取得するには、db_owner 固定データベース ロールのメンバーシップが必要です。 それ以外のすべてのユーザーについては、ソース テーブルのすべてのキャプチャ対象列に対する SELECT 権限が必要です。さらに、キャプチャ インスタンスのゲーティング ロールが定義されている場合は、そのデータベース ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、ソース テーブルに列を追加`HumanResources.Employee`し、実行、`sys.sp_cdc_get_ddl_history`ストアド プロシージャ、キャプチャ インスタンスに関連付けられているソース テーブルに適用される DDL の変更を報告する`HumanResources_Employee`です。  
  
```  
USE AdventureWorks2012;  
GO  
ALTER TABLE HumanResources.Employee  
ADD Test_Column int NULL;  
GO  
-- Pause 10 seconds to allow the event to be logged.   
WAITFOR DELAY '00:00:10';  
GO   
EXECUTE sys.sp_cdc_get_ddl_history   
    @capture_instance = 'HumanResources_Employee';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.sp_cdc_help_change_data_capture &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
