---
title: sys.filetables (TRANSACT-SQL) |Microsoft ドキュメント
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
- filetables
- filetables_TSQL
- sys.filetables
- sys.filetables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filetables catalog view
ms.assetid: a740be59-cd52-4707-9ad2-5203669a63ac
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8dde9c2f5a369c20e68135d5f4efc1d71ef2363f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33179308"
---
# <a name="sysfiletables-transact-sql"></a>sys.filetables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  各 FileTable 内の行を返します[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 FileTables について詳しくは、「[FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)」をご覧ください。    
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**||オブジェクト ID 番号。 データベース内で一意です。<br /><br /> 詳細については、 [sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)です。|  
|**is_enabled**|**bit**|1 = FileTable は "有効" 状態です。|  
|**directory_name**|**varchar(255)**|FileTable のルート ディレクトリの名前。|  
|**filename_collation_id**||FileTable に対して定義されている照合順序識別子。|  
|**filename_collation_name**||FileTable に対して定義されている照合順序名。|  
  
## <a name="see-also"></a>参照  
 [Filetable を管理します。](../../relational-databases/blob/manage-filetables.md)   
 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
  
  
