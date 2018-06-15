---
title: systranschemas (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- systranschemas
- systranschemas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systranschemas system table
ms.assetid: 864c3966-cb61-4f2b-8939-ccda112de853
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ae7ae4dc635e821b7b8cde1b54a19e6e6c5ba39c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005205"
---
# <a name="systranschemas-transact-sql"></a>systranschemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Systranschemas**トランザクションまたはスナップショット パブリケーションでパブリッシュされたアーティクルのスキーマ変更を追跡するテーブルを使用します。 このテーブルは、publication データベースと subscription データベースの両方に保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**tabid**|**int**|スキーマ変更が発生するテーブル アーティクルを指定します。|  
|**startlsn**|**[バイナリ]**|スキーマ変更開始時の LSN 値です。|  
|**endlsn**|**[バイナリ]**|スキーマ変更終了時の LSN 値です。|  
|**typeid**|**int**|スキーマ変更のタイプです。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
