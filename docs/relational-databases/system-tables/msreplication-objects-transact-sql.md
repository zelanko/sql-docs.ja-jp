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
ms.openlocfilehash: d09ff7f8a1be28c39345ecd56084ae6392ca66d8
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829886"
---
# <a name="msreplication_objects-transact-sql"></a>MSreplication_objects (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_objects**テーブルには、サブスクライバーデータベースのレプリケーションに関連付けられているオブジェクトごとに1行のデータが格納されます。 このテーブルは、サブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|パブリッシャーの名前です。|  
|**publisher_db**|**sysname**|パブリッシャーデータベースの名前。|  
|**レプリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**object_name**|**sysname**|オブジェクトの名前。|  
|**object_type**|**char(2)**|オブジェクトの種類:<br /><br /> **u** = テーブル。<br /><br /> **t** = トリガー。<br /><br /> **p** = ストアドプロシージャ。|  
|**記事**|**sysname**|オブジェクトが関連付けられているアーティクルの名前です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
