---
title: sys.sys依存 (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysdepends_TSQL
- sysdepends
- sysdepends_TSQL
- sys.sysdepends
dev_langs:
- TSQL
helpviewer_keywords:
- sysdepends system table
- sys.sysdepends compatibility view
ms.assetid: f9c182cb-386f-4e72-859f-9f1115b389f9
author: rothja
ms.author: jroth
ms.openlocfilehash: c163fb545c5eef4b1d4e10a7dcf0bfea79f3b4a9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786396"
---
# <a name="syssysdepends-transact-sql"></a>sys.sysdepends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  データベース内のオブジェクト (ビュー、プロシージャ、トリガー) 間の従属情報と、その定義に含まれるオブジェクト (テーブル、ビュー、プロシージャ) を格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|オブジェクト ID|  
|**depid**|**int**|従属しているオブジェクトの ID。|  
|**number**|**smallint**|プロシージャ番号。|  
|**depnumber**|**smallint**|従属しているプロシージャ番号。|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deptype**|**tinyint**|依存オブジェクトの種類を識別します。<br /><br /> 0 = オブジェクトまたは列 (非スキーマ バインド参照のみ)<br /><br /> 1 = オブジェクトまたは列 (スキーマバインド参照)|  
|**depdbid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**depsiteid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selall**|**bit**|1 = オブジェクトは SELECT * ステートメントで使用されます。<br /><br /> 0 = いいえ。|  
|**resultobj**|**bit**|1 = オブジェクトが更新されています。<br /><br /> 0 = いいえ。|  
|**readobj**|**bit**|1 = オブジェクトが読み取られています。<br /><br /> 0 = いいえ。|  
  
## <a name="see-also"></a>関連項目  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-sql&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sp_depends &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-depends-transact-sql.md)   
 [sql_dependencies &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
