---
title: sp_create_snapshot (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_snapshot
- sp_create_snapshot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- management data warehouse, data collector stored procedures
- data collector [SQL Server], stored procedures
- core.sp_create_snapshot stored procedure
- sp_create_snapshot
ms.assetid: ff297bda-0ee2-4fda-91c8-7000377775e3
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef2bce1ff84172d01b1304a416f84865f1cb36bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078220"
---
# <a name="coresp_create_snapshot-transact-sql"></a>sp_create_snapshot (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  管理データ ウェアハウスの core.snapshots ビューに行を挿入します。 このプロシージャは、アップロードパッケージが管理データウェアハウスへのデータのアップロードを開始するたびに呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
core.sp_create_snapshot [ @collection_set_uid = ] 'collection_set_uid'  
    , [ @collector_type_uid = ] 'collector_type_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @log_id = ] log_id  
    , [ @snapshot_id = ] snapshot_id OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [ @collection_set_uid = ]'*collection_set_uid*'  
 コレクション セットの GUID を指定します。 *collection_set_uid*は**uniqueidentifier**で、既定値はありません。 GUID を取得するには、msdb データベースの dbo.syscollector_collection_sets ビューにクエリを実行します。  
  
 [ @collector_type_uid = ]'*collector_type_uid*'  
 コレクター型の GUID。 *collector_type_uid*は**uniqueidentifier**で、既定値はありません。 GUID を取得するには、msdb データベースの dbo.syscollector_collector_types ビューにクエリを実行します。  
  
 [ @machine_name= ]'*machine_name*'  
 コレクション セットが存在するサーバーの名前を指定します。 *machine_name*は**sysname**であり、既定値はありません。  
  
 [ @named_instance= ]'*named_instance*'  
 コレクションセットのインスタンスの名前です。 *named_instance*は**sysname**であり、既定値はありません。  
  
 [ @log_id = ]*log_id*  
 データを収集したサーバー上のコレクションセットのイベントログにマップされる一意の識別子。 *log_id*は**bigint**で、既定値はありません。 *Log_id*の値を取得するには、msdb データベースの dbo. syscollector_execution_log ビューに対してクエリを実行します。  
  
 [ @snapshot_id = ]*snapshot_id*  
 コアスナップショットビューに挿入される行の一意の識別子です。 *snapshot_id*は**INT**で、出力として返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 アップロード パッケージが管理データ ウェアハウスへのデータのアップロードを開始するごとに、データ コレクターの実行時コンポーネントが core.sp_create_snapshot を呼び出します。  
  
 このプロシージャでは、次の条件がチェックされます。  
  
-   collection_set_uid が、core.source_info_internal テーブルの既存のエントリと一致していること。  
  
-   collector_type_uid が、core.supported_collector_types ビューの既存のエントリと一致していること。  
  
 上記のいずれかのチェックが失敗した場合、プロシージャは失敗し、エラーが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 **Mdw_writer** (EXECUTE 権限を持つ) 固定データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、ディスク使用量コレクション セットのスナップショットを作成し、それを管理データ ウェアハウスに追加して、スナップショット識別子を返します。 この例では、既定のインスタンスが使用されています。  
  
```  
USE <management_data_warehouse>;  
DECLARE @snapshot_id int;  
EXEC core.sp_create_snapshot   
    @collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
    @collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @machine_name = '<computername>',  
    @named_instance = 'MSSQLSERVER',  
    @log_id = 11, -- ID of the log for the collection set  
    @snapshot_id = @snapshot_id OUTPUT;  
```  
  
## <a name="see-also"></a>参照  
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データコレクターストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [管理データ ウェアハウス (management data warehouse)](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
