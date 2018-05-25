---
title: sys.dm_db_uncontained_entities (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_uncontained_entities
- dm_db_uncontained_entities_TSQL
- sys.dm_db_uncontained_entities_TSQL
- dm_db_uncontained_entities
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_uncontained_entities dynamic management view
ms.assetid: f417efd4-8c71-4f81-bc9c-af13bb4b88ad
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 18f89d3a275a36d32d72524a1c2e650a9e2dc663
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmdbuncontainedentities-transact-sql"></a>sys.dm_db_uncontained_entities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  データベースで使用される非包含オブジェクトを表示します。 非包含オブジェクトとは、包含データベースのデータベース境界を越えるオブジェクトです。 このビューは、包含データベースと非包含データベースの両方からアクセスできます。 Sys.dm_db_uncontained_entities が空の場合、データベースは、非包含エンティティを使用しません。  
  
 モジュールがデータベース境界を 2 回以上越えている場合、最初に検出された交差のみが報告されます。  
  
||||  
|-|-|-|  
|**列名**|**型**|**Description**|  
|*class*|**int**|1 = オブジェクトまたは列 (モジュール、XP、ビュー、シノニム、およびテーブルを含む)。<br /><br /> 4 = データベース プリンシパル<br /><br /> 5 = アセンブリ<br /><br /> 6 = 型<br /><br /> 7 = インデックス (フルテキスト インデックス)<br /><br /> 12 = データベース DDL トリガー<br /><br /> 19 = ルート<br /><br /> 30 = 監査の仕様|  
|*class_desc*|**nvarchar(120)**|エンティティのクラスの説明。 クラスと一致するには、次のいずれか。<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **DATABASE_PRINCIPAL**<br /><br /> **ASSEMBLY**<br /><br /> **TYPE**<br /><br /> **INDEX**<br /><br /> **DATABASE_DDL_TRIGGER**<br /><br /> **ROUTE**<br /><br /> **AUDIT_SPECIFICATION**|  
|*major_id*|**int**|エンティティの ID。<br /><br /> 場合*クラス*= 1 の場合は、object_id<br /><br /> 場合*クラス*= 4、sys.database_principals.principal_id です。<br /><br /> 場合*クラス*= 5, sys.assemblies.assembly_id です。<br /><br /> 場合*クラス*= 6, sys.types.user_type_id です。<br /><br /> 場合*クラス*= 7、sys.indexes.index_id です。<br /><br /> 場合*クラス*= 12、sys.triggers.object_id です。<br /><br /> 場合*クラス*= 19、sys.routes.route_id。<br /><br /> 場合*クラス*= 30 の場合は、sys です。 database_audit_specifications.databse_specification_id.|  
|*statement_line_number*|**int**|クラスがモジュールの場合は、非包含エンティティの使用が見つかった行番号を返します。  それ以外の場合、値は null になります。|  
|*statement_ offset_begin*|**int**|クラスがモジュールの場合は、非包含エンティティの使用が開始する開始位置 (バイト単位) が 0 で始まることを示します。 それ以外の場合、戻り値は null になります。|  
|*statement_ offset_end*|**int**|クラスがモジュールの場合は、非包含エンティティの使用の終了位置 (バイト単位) が 0 で始まることを示します。 値 -1 はモジュールの最後を表します。 それ以外の場合、戻り値は null になります。|  
|*statement_type*|**nvarchar(512)**|ステートメントの種類。|  
|*feature_ name*|**nvarchar (256)**|オブジェクトの外部名を返します。|  
|*feature_type_name*|**nvarchar (256)**|機能の種類を返します。|  
  
## <a name="remarks"></a>解説  
 sys.dm_db_uncontained_entities は、データベース境界を越える可能性のあるエンティティを示しています。 データベースの外部のオブジェクトを使用する可能性のあるユーザー エンティティが返されます。  
  
 次の機能の種類が報告されます。  
  
-   不明な包含動作 (動的な SQL または名前の遅延解決)  
  
-   DBCC コマンド  
  
-   システム ストアド プロシージャ  
  
-   システム スカラー関数  
  
-   システム テーブル値関数  
  
-   システム組み込み関数  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 sys.dm_db_uncontained_entities には、ユーザーが権限のいくつかの種類のオブジェクトのみを返します。 メンバーなど、高い特権を持つユーザーでは、この機能を使用する必要があります、データベースの包含を完全に評価する、 **sysadmin**固定サーバー ロールまたは**db_owner**ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、P1 という名前のプロシージャを作成し、 `sys.dm_db_uncontained_entities`にクエリを実行します。 このクエリは、P1 がデータベースの外部にある **sys.endpoints** を使用していることを報告します。  
  
```sql  
CREATE DATABASE Test;  
GO  
  
USE Test;  
GO  
CREATE PROC P1  
AS   
SELECT * FROM sys.endpoints ;  
GO  
SELECT SO.name, UE.* FROM sys.dm_db_uncontained_entities AS UE  
LEFT JOIN sys.objects AS SO  
    ON UE.major_id = SO.object_id;  
```  
  
## <a name="see-also"></a>参照  
 [包含データベース](../../relational-databases/databases/contained-databases.md)  
  
  
