---
title: sys.column_type_usages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- column_type_usages
- sys.column_type_usages_TSQL
- column_type_usages_TSQL
- sys.column_type_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_type_usages catalog view
ms.assetid: 1ead375e-f662-4837-903f-8947496c51e4
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ef7e360d755d02b37a8146c4ba4fa881b009c469
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syscolumntypeusages-transact-sql"></a>sys.column_type_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ユーザー定義型の列ごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|この列が属するオブジェクトの ID です。|  
|**column_id**|**int**|列の ID です。 オブジェクト内で一意です。|  
|**user_type_id**|**int**|ユーザー定義データ型の ID。<br /><br /> 型の名前を返すに参加させる、 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログをこの列に表示します。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スカラー型カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
