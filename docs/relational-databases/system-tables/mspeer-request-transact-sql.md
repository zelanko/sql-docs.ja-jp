---
title: MSpeer_request (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_request
- MSpeer_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_request system table
ms.assetid: ed048c46-7a2f-4ad0-bc7c-c2d65e83b4fb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 904919bfac6dc9fc0c5bf638605d363eba5a68f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63026375"
---
# <a name="mspeerrequest-transact-sql"></a>MSpeer_request (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  MSpeer_request テーブルは、指定されたパブリケーションに対する状態要求を追跡するために、ピア ツー ピア レプリケーションで使用されます。 このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**int**|要求を識別します。|  
|パブリケーション (publication)|**sysname**|状態要求の開始をパブリケーションの名前です。|  
|sent_date|**datetime**|状態要求が開始された日付と時刻|  
|description|**nvarchar (4000)**|個々 の状態要求を識別するために使用できるユーザー定義情報。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
