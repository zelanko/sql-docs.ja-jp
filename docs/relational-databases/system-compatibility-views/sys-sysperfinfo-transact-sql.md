---
title: sys.sysperfinfo (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 40
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0af9af8434b368c62d109942b806c9bb803d058a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
