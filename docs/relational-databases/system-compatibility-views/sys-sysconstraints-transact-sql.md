---
title: sys.sysの制約 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
author: rothja
ms.author: jroth
ms.openlocfilehash: b3ee1ce24876eab6689da7432329a2788ce70c34
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85663353"
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysの制約 (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  データベース内の制約を所有するオブジェクトへの制約のマッピングが含まれます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|制約番号。|  
|**id**|**int**|制約を所有するテーブルの ID。|  
|**colid**|**smallint**|制約が定義されている列の ID。<br /><br /> 0 = テーブル制約|  
|**spare1**|**tinyint**|予約されています。|  
|**status**|**int**|ステータスを示す擬似ビットマスク。 次の値があります。<br /><br /> 1 = PRIMARY KEY 制約<br /><br /> 2 = UNIQUE KEY 制約<br /><br /> 3 = FOREIGN KEY 制約<br /><br /> 4 = CHECK 制約<br /><br /> 5 = DEFAULT 制約<br /><br /> 16 = 列レベル制約<br /><br /> 32 = テーブルレベルの制約|  
|**actions**|**int**|予約されています。|  
|**error**|**int**|予約されています。|  
  
## <a name="see-also"></a>関連項目  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
