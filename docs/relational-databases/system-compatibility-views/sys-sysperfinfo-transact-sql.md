---
title: "sys.sysperfinfo (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 92d1cb29e339017f13c5b784f2b1459cf1a19432
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  含まれています、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Windows システム モニターで表示できる内部パフォーマンス カウンターの表現。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|パフォーマンス オブジェクト名など**SQLServer:LockManager**または**SQLServer:BufferManager**です。|  
|**counter_name**|**nchar(128)**|オブジェクトの内部パフォーマンス カウンターの名前など**ページ要求**または**Locks Requested**です。|  
|**instance_name**|**nchar(128)**|カウンターの名前付きインスタンス。 たとえばなどのロックの種類ごとに保持されるカウンターが**テーブル**、**ページ**、**キー**のようにします。 類似したカウンターはインスタンス名で区別されます。|  
|**cntr_value**|**bigint**|実際のカウンター値。 多くの場合、これは、インスタンス イベントの発生数を表すレベルまたは単純増加のカウンターになります。|  
|**cntr_type**|**int**|Windows パフォーマンス アーキテクチャによって定義されるカウンターの種類。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
