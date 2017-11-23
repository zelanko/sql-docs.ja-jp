---
title: "sys.sysdepends (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sysdepends_TSQL
- sysdepends
- sysdepends_TSQL
- sys.sysdepends
dev_langs: TSQL
helpviewer_keywords:
- sysdepends system table
- sys.sysdepends compatibility view
ms.assetid: f9c182cb-386f-4e72-859f-9f1115b389f9
caps.latest.revision: "43"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 76a51f07ef8b504c616cd4ef080d0c84e9f782a5
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syssysdepends-transact-sql"></a>sys.sysdepends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース内のオブジェクト (ビュー、プロシージャ、トリガー) 間の従属情報と、その定義に含まれるオブジェクト (テーブル、ビュー、プロシージャ) を格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|オブジェクト id です。|  
|**depid**|**int**|従属しているオブジェクトの ID。|  
|**数**|**smallint**|プロシージャ番号。|  
|**depnumber**|**smallint**|従属しているプロシージャ番号。|  
|**ステータス**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deptype**|**tinyint**|依存オブジェクト型を識別します。<br /><br /> 0 = オブジェクトまたは列 (非スキーマ バインド参照のみ)<br /><br /> 1 = オブジェクトまたは列 (スキーマ バインド参照)|  
|**depdbid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**depsiteid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selall**|**bit**|1 = オブジェクトは SELECT * ステートメントで使用されます。<br /><br /> 0 = いいえ。|  
|**resultobj**|**bit**|1 = オブジェクトが更新されます。<br /><br /> 0 = いいえ。|  
|**readobj**|**bit**|1 = オブジェクトが読み取られます。<br /><br /> 0 = いいえ。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;です。TRANSACT-SQL と #41 です。](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sp_depends &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-depends-transact-sql.md)   
 [sys.sql_dependencies &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
