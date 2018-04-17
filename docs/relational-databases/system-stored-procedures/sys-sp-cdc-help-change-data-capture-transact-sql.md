---
title: sys.sp_cdc_help_change_data_capture (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_change_data_capture_TSQL
- sys.sp_cdc_help_change_data_capture_TSQL
- sp_cdc_help_change_data_capture
- sys.sp_cdc_help_change_data_capture
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], querying metadata
- sys.sp_cdc_help_change_data_capture
- sp_cdc_help_change_data_capture
ms.assetid: 91fd41f5-1b4d-44fe-a3b5-b73eff65a534
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 637b9edcc51832e37289057e4513ca18f30ef446
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysspcdchelpchangedatacapture-transact-sql"></a>sys.sp_cdc_help_change_data_capture (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベース内で変更データ キャプチャが有効にされている各テーブルを対象に、変更データ キャプチャの構成を返します。 取得できる行は、1 つのソース テーブルにつき最大 2 行 (キャプチャ インスタンスごとに 1 行) です。 変更データ キャプチャは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディッションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](../../sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_help_change_data_capture   
  [ [ @source_schema = ] 'source_schema' ]  
  [, [ @source_name = ] 'source_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @source_schema =] '*source_schema*'  
 ソース テーブルが属するスキーマの名前です。 *source_schema*は**sysname**、既定値は NULL です。 ときに*source_schema*が指定されている*source_name*も指定する必要があります。  
  
 Null 以外の場合、 *source_schema*現在のデータベースに存在する必要があります。  
  
 場合*source_schema* NULL 以外の場合は、 *source_name* NULL 以外である必要があります。  
  
 [ @source_name =] '*source_name*'  
 ソース テーブルの名前です。 *source_name*は**sysname**、既定値は NULL です。 ときに*source_name*が指定されている*source_schema*も指定する必要があります。  
  
 Null 以外の場合、 *source_name*現在のデータベースに存在する必要があります。  
  
 場合*source_name* NULL 以外の場合は、 *source_schema* NULL 以外である必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|ソース テーブルのスキーマ名です。|  
|source_table|**sysname**|ソース テーブルの名前です。|  
|capture_instance|**sysname**|キャプチャ インスタンスの名前です。|  
|object_id|**int**|ソース テーブルに関連付けられている変更テーブルの ID です。|  
|source_object_id|**int**|ソース テーブルの ID です。|  
|start_lsn|**binary(10)**|変更テーブルをクエリする際の下端を表すログ シーケンス番号 (LSN) です。<br /><br /> NULL = 下端は設定されていません。|  
|end_lsn|**binary(10)**|変更テーブルをクエリする際の上端を表す LSN です。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、この列は常に NULL です。|  
|supports_net_changes|**bit**|差分変更のサポートが有効になっています。|  
|has_drop_pending|**bit**|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では使用されません。|  
|role_name|**sysname**|変更データへのアクセスを制御するデータベース ロールの名前です。<br /><br /> NULL = ロールは使用されません。|  
|index_name|**sysname**|ソース テーブル内の行を一意に識別するためのインデックス名です。|  
|filegroup_name|**sysname**|変更テーブルが存在するファイル グループの名前です。<br /><br /> NULL = 変更テーブルは、データベースの既定のファイル グループに存在します。|  
|create_date|**datetime**|キャプチャ インスタンスが有効にされた日付です。|  
|index_column_list|**nvarchar(max)**|ソース テーブル内の行を一意に識別するためのインデックス列のリストです。|  
|captured_column_list|**nvarchar(max)**|キャプチャ対象のソース列のリスト。|  
  
## <a name="remarks"></a>解説  
 ときに両方*source_schema*と*source_name*既定で NULL の場合、または、NULL を明示的に設定されてこのストアド プロシージャは、呼び出し元が選択できるキャプチャ インスタンス、データベースのすべての情報を返しますアクセスします。 ときに*source_schema*と*source_name*は NULL 以外で、特定の名前付きの有効なテーブルに関する情報のみが返されます。  
  
## <a name="permissions"></a>権限  
 ときに*source_schema*と*source_name*が NULL の場合、呼び出し元の承認は、有効なテーブルは、結果セットに含まれるを決定します。 呼び出し元には、キャプチャ インスタンスのすべてのキャプチャ対象列に対する SELECT 権限が必要です。さらに、テーブル情報を含める場合は、定義されたすべてのゲーティング ロールのメンバーシップも必要です。 db_owner データベース ロールのメンバーは、定義されたすべてのキャプチャ インスタンスに関する情報を表示できます。 特定の有効なテーブルの情報を要求する場合は、指定したテーブルについて、同じ SELECT およびメンバーシップ基準が適用されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-change-data-capture-configuration-information-for-a-specified-table"></a>A. 指定したテーブルについて変更データ キャプチャの構成情報を取得する  
 次の例は、`HumanResources.Employee` テーブルを対象に変更データ キャプチャの構成を取得します。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee';  
GO  
```  
  
### <a name="b-returning-change-data-capture-configuration-information-for-all-tables"></a>B. すべてのテーブルについて変更データ キャプチャの構成情報を取得する  
 次の例は、呼び出し元がアクセスを許可されている変更データを含むデータベース内のすべての有効なテーブルを対象に構成情報を取得します。  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture;  
GO  
```  
  
  
