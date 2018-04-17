---
title: core.sp_purge_data (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
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
- sp_purge_data_TSQL
- sp_purge_data
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_data
- management data warehouse, data collector stored procedures
- core.sp_purge_data stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 056076c3-8adf-4f51-8a1b-ca39696ac390
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b929306a5f865defa4c264c289c4525694784c1b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="coresppurgedata-transact-sql"></a>core.sp_purge_data (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  保有ポリシーに基づいて、管理データ ウェアハウスからデータを削除します。 このプロシージャは、mdw_purge_data によって毎日実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]管理データ ウェアハウスに対して、エージェント ジョブは、指定されたインスタンスに関連付けられています。 このストアド プロシージャを使用すると、要求に応じて管理データ ウェアハウスからデータを削除できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
core.sp_purge_data  
    [ [ @retention_days = ] retention_days ]  
    [ , [ @instance_name = ] 'instance_name' ]  
    [ , [ @collection_set_uid = ] 'collection_set_uid' ]  
    [ , [ @duration = ] duration ]  
```  
  
## <a name="arguments"></a>引数  
 [@retention_days =] *retention_days*  
 データを管理データ ウェアハウスのテーブルに保管しておく日数を指定します。 古いタイムスタンプを持つデータ*retention_days*を削除します。 *retention_days*は**smallint**、既定値は NULL です。 指定する場合、値は正数にする必要があります。 NULL の場合は、core.snapshots ビューの valid_through 列の値によって、削除対象の行が判断されます。  
  
 [@instance_name =] '*instance_name*'  
 コレクション セットのインスタンスの名前を指定します。 *instance_name*は**sysname**、既定値は NULL です。  
  
 *instance_name* 、完全修飾名、コンピューター名と形式でインスタンス名で構成される必要があります*computername*\\*instancename*です。 NULL の場合は、ローカル サーバーの既定のインスタンスが使用されます。  
  
 [@collection_set_uid =] '*collection_set_uid*'  
 コレクション セットの GUID を指定します。 *collection_set_uid*は**uniqueidentifier**、既定値は NULL です。 NULL の場合は、すべてのコレクション セットから条件を満たす行が削除されます。 この値を取得するには、syscollector_collection_sets カタログ ビューに対してクエリを実行します。  
  
 [@duration =]*期間*  
 パージ操作を実行する最大時間を分単位で指定します。 *期間*は**smallint**、既定値は NULL です。 指定する場合、値はゼロまたは正の整数にする必要があります。 NULL の場合は、条件を満たすすべての行が削除されるか操作が手動で停止されるまで、操作は実行されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 このプロシージャでは、保有期間に基づいて削除対象となる core.snapshots ビューの行が選択されます。 削除対象となるすべての行が core.snapshots_internal テーブルから削除されます。 先行する行が削除されると、管理データ ウェアハウスのすべてのテーブルでカスケード削除操作が実行されます。 これは、収集されたデータを格納するすべてのテーブルに対して定義されている ON DELETE CASCADE 句を使って実行されます。  
  
 各スナップショットとその関連データは、明示的なトランザクションで削除されてからコミットされます。 そのため、パージ操作を手動で停止すると、または指定した値のかどうかは@durationが経過すると、コミットされていないデータのみが残ります。 このデータは、ジョブの次回の実行時に削除できます。  
  
 このプロシージャは、管理データ ウェアハウス データベースのコンテキストで実行してください。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **mdw_admin** (EXECUTE 権限) を持つ固定データベース ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-running-sppurgedata-with-no-parameters"></a>A. パラメーターなしで sp_purge_data を実行する  
 次の例では、パラメーターを指定せずに core.sp_purge_data を実行します。 そのため、すべてのパラメーターに既定値の NULL が使用され、それに関連付けられている動作が実行されます。  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data;  
GO  
```  
  
### <a name="b-specifying-retention-and-duration-values"></a>B. 保有期間と実行時間の値を指定する  
 次の例では、7 日を経過したデータを管理データ ウェアハウスから削除します。 さらに、@durationパラメーターが指定されるため、操作を 5 分以内に実行されます。  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data @retention_days = 7, @duration = 5;  
GO  
```  
  
### <a name="c-specifying-an-instance-name-and-collection-set"></a>C. インスタンス名とコレクション セットを指定する  
 次の例は、設定の指定したインスタンスに指定したコレクションの管理データ ウェアハウスからデータを削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 @retention_daysが指定されていない、core.snapshots ビューの valid_through 列の値は削除対象のコレクション セットの行を判断に使用します。  
  
```  
USE <management_data_warehouse>;  
GO  
-- Get the collection set unique identifier for the Disk Usage system collection set.  
DECLARE @disk_usage_collection_set_uid uniqueidentifier = (SELECT collection_set_uid   
    FROM msdb.dbo.syscollector_collection_sets WHERE name = N'Disk Usage');   
  
EXECUTE core.sp_purge_data @instance_name = @@SERVERNAME, @collection_set_uid = @disk_usage_collection_set_uid;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
