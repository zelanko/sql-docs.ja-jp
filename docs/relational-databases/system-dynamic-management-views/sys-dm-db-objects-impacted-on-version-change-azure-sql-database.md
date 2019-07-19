---
title: sys.dm_db_objects_impacted_on_version_change (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_objects_impacted_on_version_change_TSQL
- dm_db_objects_impacted_on_version_change
- dm_db_objects_impacted_on_version_change_TSQL
- sys.dm_db_objects_impacted_on_version_change
dev_langs:
- TSQL
helpviewer_keywords:
- dm_db_objects_impacted_on_version_change
- sys.dm_db_objects_impacted_on_version_change
ms.assetid: b94af834-c4f6-4a27-80a6-e8e71fa8793a
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 9934771b6a887f6ae0984e79ce11729145e3d410
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051539"
---
# <a name="sysdmdbobjectsimpactedonversionchange-azure-sql-database"></a>sys.dm_db_objects_impacted_on_version_change (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  このデータベース スコープのシステム ビューがメジャー リリースのアップグレードに影響を受けるオブジェクトを検出する早期警告システムを提供するように設計[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。 このビューを使用すると、アップグレードの前または後に、影響を受けるすべてのオブジェクトのリストを取得できます。 サーバー全体で完全なアカウンティングを取得するには、各データベースでは、このビューをクエリする必要があります。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|class|**int** NOT NULL|影響を受けるオブジェクトのクラス。<br /><br /> **1** = 制約<br /><br /> **7** = インデックスとヒープ|  
|class_desc|**nvarchar(60)** NOT NULL|クラスの説明です。<br /><br /> **OBJECT_OR_COLUMN**<br /><br /> **INDEX**|  
|major_id|**int** NOT NULL|制約のオブジェクト ID、あるいはインデックスまたはヒープを含んでいるテーブルのオブジェクト ID。|  
|minor_id|**int** NULL|**NULL**制約<br /><br /> インデックスとヒープの場合は Index_id|  
|依存関係|**nvarchar(60)** NOT NULL|制約またはインデックスが影響を受ける原因となっている依存関係の説明。 同じの値は、アップグレード中に生成される警告も使用されます。<br /><br /> 例 :<br /><br /> **領域**(の組み込み)<br /><br /> **geometry** (システム UDT) の<br /><br /> **geography::parse** (システム UDT のメソッド) の|  
  
## <a name="permissions"></a>アクセス許可  
 VIEW DATABASE STATE 権限が必要です。  
  
## <a name="example"></a>例  
 次の例ではクエリを示します**sys.dm_db_objects_impacted_on_version_change**次の主要なサーバー バージョンへのアップグレードによって影響を受けるオブジェクトを検索するには  
  
```  
SELECT * FROM sys.dm_db_objects_disabled_on_version_change;  
GO  
```  
  
```  
class  class_desc        major_id    minor_id    dependency                       
------ ----------------- ----------- ----------- ----------   
1      OBJECT_OR_COLUMN  181575685   NULL        geometry                        
7      INDEX             37575172    1           geometry                        
7      INDEX             2121058592  1           geometry                        
1      OBJECT_OR_COLUMN  101575400   NULL        geometry     
```  
  
## <a name="remarks"></a>コメント  
  
### <a name="how-to-update-impacted-objects"></a>影響を受けるオブジェクトを更新する方法  
 次の手順は、次の 6 月のサービス リリースのアップグレード後に行う必要のある修正措置を説明しています。  
  
|[オーダー]|影響を受けるオブジェクト|修正措置|  
|-----------|---------------------|-----------------------|  
|1|**[インデックス]**|識別されるインデックスを再構築**sys.dm_db_objects_impacted_on_version_change**例。  `ALTER INDEX ALL ON <table> REBUILD`<br />または<br />`ALTER TABLE <table> REBUILD`|  
|2|**Object**|識別されるすべての制約**sys.dm_db_objects_impacted_on_version_change**基になるテーブル内の geometry と geography データが再計算した後に再検証する必要があります。 制約、ALTER TABLE を使用して再検証します。 <br />以下に例を示します。 <br />`ALTER TABLE <tab> WITH CHECK CHECK CONSTRAINT <constraint name>`<br />または<br />`ALTER TABLE <tab> WITH CHECK CONSTRAINT ALL`|  
  
  
