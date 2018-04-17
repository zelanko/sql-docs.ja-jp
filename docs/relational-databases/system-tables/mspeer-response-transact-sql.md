---
title: MSpeer_response (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSpeer_response
- MSpeer_response_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_response system table
ms.assetid: 510e24cf-0292-47a9-b1d9-71a30fef030f
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8e095e2602c791693954f7400e32c1075d4ed206
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mspeerresponse-transact-sql"></a>MSpeer_response (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSpeer_response**テーブルがパブリケーション状態要求に対する各ノードの応答を格納するピア ツー ピア レプリケーションで使用します。 このテーブルは、パブリケーション データベース内に保存されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|内の状態要求エントリを識別、 [MSpeer_request](../../relational-databases/system-tables/mspeer-request-transact-sql.md)テーブル。|  
|**ピア**|**sysname**|応答を生成したピアです。|  
|**peer_db**|**sysname**|応答を生成したピア側のサブスクリプション データベースです。|  
|**received_date**|**datetime**|ピア要求を受信した日付と時刻です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
