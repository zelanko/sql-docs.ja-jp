---
title: cdc.lsn_time_mapping (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- cdc.lsn_time_mapping
- cdc.lsn_time_mapping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.lsn_time_mapping
ms.assetid: 1cb7aedc-48a4-486e-9b91-d30c4bd4084e
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 402443b42a44131e023923267d34b322e3c0c670
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39102630"
---
# <a name="cdclsntimemapping-transact-sql"></a>cdc.lsn_time_mapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更テーブル内に行が存在する各トランザクションについて 1 行を返します。 このテーブルは、ログ シーケンス番号 (LSN) のコミット値と、トランザクションがコミットされた時刻とをマップするために使用されます。 変更テーブルのエントリが存在しない場合にエントリを記録することもできます。 これにより、変更アクティビティが少ないか、まったくない場合に、LSN 処理の完了をテーブルに記録できます。  
  
 システム テーブルに対して直接クエリを実行することは、できるだけ避けてください。 代わりに、実行、 [sys.fn_cdc_map_lsn_to_time &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md)と[sys.fn_cdc_map_time_to_lsn &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)システム関数。  
    
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**start_lsn**|**binary(10)**|コミットされたトランザクションの LSN。|  
|**tran_begin_time**|**datetime**|LSN に関連付けられたトランザクションの開始時刻。|  
|**tran_end_time**|**datetime**|トランザクションの終了時刻。|  
|**tran_id**|**varbinary(10)**|トランザクションの ID。|  
  
## <a name="see-also"></a>参照  
 [トランザクション ログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [cdc です。&#60;capture_instance&#62;_CT &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
  
  
