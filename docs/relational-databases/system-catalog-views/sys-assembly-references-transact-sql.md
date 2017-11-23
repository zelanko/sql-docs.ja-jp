---
title: "sys.assembly_references (TRANSACT-SQL) |Microsoft ドキュメント"
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
- assembly_references
- sys.assembly_references_TSQL
- assembly_references_TSQL
- sys.assembly_references
dev_langs: TSQL
helpviewer_keywords: sys.assembly_references catalog view
ms.assetid: 50a5ed42-2d5b-4a11-a0d2-9a02241b078d
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 19030a17f6f02e87c6b513267050b9828ada63d3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysassemblyreferences-transact-sql"></a>sys.assembly_references (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つのアセンブリが直接他方を参照している、アセンブリのペアごとに 1 行のデータを保持します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|参照しているアセンブリの ID です。|  
|**referenced_assembly_id**|**int**|参照されているアセンブリの ID です。|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [CLR アセンブリ カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
