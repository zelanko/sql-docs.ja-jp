---
title: MSpeer_request (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1d24825e87c65e998d00a02339f07b6f87b27175
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824867"
---
# <a name="mspeer_request-transact-sql"></a>MSpeer_request (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  MSpeer_request テーブルは、ピアツーピアレプリケーションで、特定のパブリケーションに対する状態要求を追跡するために使用されます。 このテーブルは、パブリケーションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|id|**int**|要求を識別します。|  
|パブリケーション (publication)|**sysname**|ステータス要求が開始されたパブリケーションの名前。|  
|sent_date|**datetime**|状態要求が開始された日付と時刻|  
|description|**nvarchar (4000)**|個々の状態要求を識別するために使用できるユーザー定義の情報。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
