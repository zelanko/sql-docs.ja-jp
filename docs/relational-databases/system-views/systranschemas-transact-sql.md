---
title: systranschemas (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- systranschemas
- systranschemas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systranschemas system table
ms.assetid: 864c3966-cb61-4f2b-8939-ccda112de853
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3339cf1731c712cdfee7145390d5cc955c748a98
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62693626"
---
# <a name="systranschemas-transact-sql"></a>systranschemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Systranschemas**トランザクションまたはスナップショット パブリケーションでパブリッシュされたアーティクルのスキーマ変更を追跡するテーブルを使用します。 このテーブルは、publication データベースと subscription データベースの両方に保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tabid**|**int**|スキーマの変更が発生したテーブル アーティクルを識別します。|  
|**startlsn**|**[バイナリ]**|スキーマ変更開始時の LSN 値です。|  
|**endlsn**|**[バイナリ]**|スキーマ変更の最後の LSN 値です。|  
|**typeid**|**int**|スキーマ変更のタイプです。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
