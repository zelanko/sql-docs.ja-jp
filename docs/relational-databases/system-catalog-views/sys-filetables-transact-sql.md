---
title: "sys.filetables (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- filetables
- filetables_TSQL
- sys.filetables
- sys.filetables_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.filetables catalog view
ms.assetid: a740be59-cd52-4707-9ad2-5203669a63ac
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0b047ba0650302857775b62214a7771c7e1f6a0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysfiletables-transact-sql"></a>sys.filetables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  各 FileTable 内の行を返します[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 Filetable の詳細については、次を参照してください。 [Filetable &#40;です。SQL Server &#41;](../../relational-databases/blob/filetables-sql-server.md).    
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**||オブジェクト ID 番号。 データベース内で一意です。<br /><br /> 詳細については、 [sys.objects &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**is_enabled**|**bit**|1 = FileTable は "有効" 状態です。|  
|**directory_name**|**varchar (255)**|FileTable のルート ディレクトリの名前。|  
|**filename_collation_id**||FileTable に対して定義されている照合順序識別子。|  
|**filename_collation_name**||FileTable に対して定義されている照合順序名。|  
  
## <a name="see-also"></a>参照  
 [Filetable を管理します。](../../relational-databases/blob/manage-filetables.md)   
 [FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
  
  
