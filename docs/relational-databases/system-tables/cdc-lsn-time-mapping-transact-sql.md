---
title: cdc. lsn_time_mapping (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- cdc.lsn_time_mapping
- cdc.lsn_time_mapping_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cdc.lsn_time_mapping
ms.assetid: 1cb7aedc-48a4-486e-9b91-d30c4bd4084e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1e89e67b49498320e4500b99332fc5584d5f38d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68066669"
---
# <a name="cdclsn_time_mapping-transact-sql"></a>cdc. lsn_time_mapping (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  変更テーブル内の行を保持しているトランザクションごとに1行の値を返します。 このテーブルは、ログシーケンス番号 (LSN) のコミット値とトランザクションがコミットされた時刻の間のマッピングに使用されます。 変更テーブルエントリがないエントリもログに記録される場合があります。 これにより、変更アクティビティが少ないか、まったくない場合に、LSN 処理の完了をテーブルに記録できます。  
  
 システムテーブルに対して直接クエリを実行しないことをお勧めします。 代わりに、transact-sql &#40;システム関数を[&#41;transact-sql&#41;fn_cdc_map_time_to_lsn](../../relational-databases/system-functions/sys-fn-cdc-map-time-to-lsn-transact-sql.md)および &#40;を実行して、 [fn_cdc_map_lsn_to_time](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md)を実行します。  
    
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**start_lsn**|**binary (10)**|コミットされたトランザクションの LSN。|  
|**tran_begin_time**|**DATETIME**|LSN に関連付けられているトランザクションが開始された時刻。|  
|**tran_end_time**|**DATETIME**|トランザクションが終了した時刻。|  
|**tran_id**|**varbinary (10)**|トランザクションの ID。|  
  
## <a name="see-also"></a>参照  
 [トランザクションログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [cdc. &#60;capture_instance&#62;_CT &#40;Transact-sql&#41;](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md)  
  
  
