---
title: core.sp_update_data_source を呼び出します (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
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
- sp_update_data_source
- sp_update_data_source_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_data_source
- management data warehouse, data collector stored procedures
- core.sp_update_data_source stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 66b95f96-6df7-4657-9b3c-86a58c788ca5
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10ea691202d475c8a79f769a739edfc1f106b277
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="corespupdatedatasource-transact-sql"></a>core.sp_update_data_source (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  管理データ ウェアハウスの core.source_info_internal テーブルで既存行の更新または新規行の挿入を行います。 このプロシージャは、アップロード パッケージが管理データ ウェアハウスへのデータのアップロードを開始するたびに、データ コレクターの実行時コンポーネントによって呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
core.sp_update_data_source [ @collection_set_uid = ] 'collection_set_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @days_until_expiration = ] days_until_expiration  
    , [ @source_id = ] source_id OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [ @collection_set_uid =] '*collection_set_uid*'  
 コレクション セットの GUID を指定します。 *collection_set_uid*は**uniqueidentifier**既定値はありません。 GUID を取得するには、msdb データベースの dbo.syscollector_collection_sets ビューにクエリを実行します。  
  
 [ @machine_name =] '*machine_name*'  
 コレクション セットが存在するサーバーの名前を指定します。 *コンピューター名*は**sysname**既定値はありません。  
  
 [ @named_instance =] '*named_instance*'  
 コレクション セットのインスタンスの名前を指定します。 *named_instance*は**sysname**既定値はありません。  
  
> [!NOTE]  
>  *named_instance* 、完全修飾名、コンピューター名と形式でインスタンス名で構成される必要があります*computername*\\*instancename*です。  
  
 [ @days_until_expiration = ] *days_until_expiration*  
 スナップショット データ保持期間の日数を指定します。 *days_until_expiration*は**smallint**です。  
  
 [ @source_id =] *source_id*  
 更新元の一意な識別子を指定します。 *source_id*は**int**出力として返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 アップロード パッケージが管理データ ウェアハウスへのデータのアップロードを開始するたびに、データ コレクターの実行時コンポーネントが core.sp_update_data_source を呼び出します。 前回のアップロード時以降に次のいずれかの変更が行われている場合は、core.source_info_internal テーブルが更新されます。  
  
-   新しいコレクション セットが追加された。  
  
-   days_until_expiration の値が変更された。  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **mdw_writer** (EXECUTE 権限) を持つ固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、データ ソース (この場合はディスク使用量コレクション セット) を更新し、有効期限 (日数) を設定します。さらに、更新元の識別子を返します。 この例では、既定のインスタンスを使用しています。  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @source_id int;  
EXEC core.sp_update_data_source   
@collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
@machine_name = '<computername>',  
@named_instance = 'MSSQLSERVER',  
@days_until_expiration = 10,  
@source_id = @source_id OUTPUT;  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [管理データ ウェアハウス](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
