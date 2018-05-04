---
title: MSpeer_conflictdetectionconfigrequest (TRANSACT-SQL) |Microsoft ドキュメント
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
- MSpeer_conflictdetectionconfigrequest_TSQL
- MSpeer_conflictdetectionconfigrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigurerequest
ms.assetid: 83afa0ca-707e-4468-a888-228268ed4e10
caps.latest.revision: 11
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6f4b5918797cee78394384a37d707b72de5620d0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mspeerconflictdetectionconfigrequest-transact-sql"></a>MSpeer_conflictdetectionconfigrequest (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ピア ツー ピア レプリケーションで、パブリケーションに対するトポロジ全体の構成要求を追跡するために使用されます。 このテーブルは、パブリケーション データベース内に保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|競合構成要求を識別します。 Request_id 列に[MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md)はこの値を使用します。|  
|パブリケーション (publication)|**sysname**|競合構成要求が発行されたパブリケーションの名前です。|  
|sent_date|**datetime**|競合構成要求が開始された日時です。|  
|timeout|**int**|すべてのピアから競合情報が返されるのをプロシージャが待機する時間です。|  
|modified_date|**datetime**|フェーズが完了した日時です。|  
|progress_phase|**nvarchar(32)**|処理の現在のフェーズを識別します。有効値は次のとおりです。<br /><br /> Started<br /><br /> トポロジの調査<br /><br /> 状態の収集<br /><br /> 収集された状態|  
|phase_timed_out|**bit**|現在のフェーズがタイムアウトしたかどうかを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
