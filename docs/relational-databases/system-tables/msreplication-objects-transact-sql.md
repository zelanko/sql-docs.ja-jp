---
title: MSreplication_objects (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9745b6eb1a906297f1ed8324f840914cc871f251
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722935"
---
# <a name="msreplication_objects-transact-sql"></a>MSreplication_objects (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **MSreplication_objects**テーブルには、サブスクライバーデータベースのレプリケーションに関連付けられているオブジェクトごとに1行のデータが格納されます。 このテーブルは、サブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|パブリッシャーの名前です。|  
|**publisher_db**|**sysname**|パブリッシャーデータベースの名前。|  
|**レプリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**object_name**|**sysname**|オブジェクトの名前。|  
|**object_type**|**char(2)**|オブジェクトの種類:<br /><br /> **u** = テーブル。<br /><br /> **t** = トリガー。<br /><br /> **p** = ストアドプロシージャ。|  
|**記事**|**sysname**|オブジェクトが関連付けられているアーティクルの名前です。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
