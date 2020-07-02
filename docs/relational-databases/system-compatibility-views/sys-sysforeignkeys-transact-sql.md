---
title: sys.sysforeignkeys (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysforeignkeys
- sys.sysforeignkeys
- sys.sysforeignkeys_TSQL
- sysforeignkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysforeignkeys system table
- sys.sysforeignkeys compatibility view
ms.assetid: 41544236-1c46-4501-be88-18c06963b6e8
author: rothja
ms.author: jroth
ms.openlocfilehash: e6b3d1e89e09c0243c1329c724b9907e7c5f50b7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786353"
---
# <a name="syssysforeignkeys-transact-sql"></a>sys.sysforeignkeys (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  データベース中のテーブルの定義内にある、FOREIGN KEY 制約に関する情報を保持します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|外部キー制約の ID。|  
|**fkeyid**|**int**|FOREIGN KEY 制約を持つテーブルのオブジェクト ID。|  
|**rkeyid**|**int**|FOREIGN KEY 制約で参照されているテーブルのオブジェクト ID。|  
|**fkey**|**smallint**|参照している列の ID。|  
|**rkey**|**smallint**|参照されている列の ID。|  
|**keyno**|**smallint**|参照列リスト内の列の位置。|  
  
## <a name="see-also"></a>関連項目  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
