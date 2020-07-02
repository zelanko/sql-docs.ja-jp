---
title: MSpeer_response (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_response
- MSpeer_response_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_response system table
ms.assetid: 510e24cf-0292-47a9-b1d9-71a30fef030f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6f256fdf082e38aca85d1a002af13c8892f810de
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764134"
---
# <a name="mspeer_response-transact-sql"></a>MSpeer_response (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  **MSpeer_response**テーブルは、ピアツーピアレプリケーションで、各ノードの応答をパブリケーションステータス要求に格納するために使用されます。 このテーブルは、パブリケーションデータベースに格納されます。  
  
## <a name="definition"></a>定義  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**request_id**|**int**|[MSpeer_request](../../relational-databases/system-tables/mspeer-request-transact-sql.md)テーブル内の状態要求エントリを識別します。|  
|**家**|**sysname**|応答を生成したピア。|  
|**peer_db**|**sysname**|応答を生成したピアのサブスクリプションデータベース。|  
|**received_date**|**datetime**|ピア要求を受信した日付と時刻。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
