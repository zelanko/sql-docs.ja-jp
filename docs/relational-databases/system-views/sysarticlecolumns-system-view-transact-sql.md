---
title: "sysarticlecolumns (システム ビュー) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs: TSQL
helpviewer_keywords: sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
caps.latest.revision: "10"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a7e5f8c29826bd37306fe2fc455b449ab6362c67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (システム ビュー) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticlecolumns**ビューは、パブリッシュされたアーティクル内の列に関する追加情報を公開します。 このビューは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|アーティクルの識別子です。|  
|**返された colid**|**int**|アーティクル内の列の識別子。|  
|**is_udt**|**int**|列がユーザー定義データ型 (UDT) 列であるかどうかを示します。 値**1** UDT 列を示します。|  
|**is_xml**|**int**|列が、 **xml**列です。 値**1**を示す、 **xml**列です。|  
|**is_max**|**int**|列が大きな値データ型の列は、(**varchar (max)**、 **nvarchar (max)**または**varbinary (max)**)。 値**1**大きな値の列を示します。|  
  
## <a name="see-also"></a>参照  
 [sp_articlecolumn (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
