---
title: "sys.pdw_loader_run_stages (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d209fff76a89f84b67e351864b102ebf8ecbcd5f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwloaderrunstages-transact-sql"></a>sys.pdw_loader_run_stages (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  進行中と完了したロード操作に関する情報を含む[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。 情報は、システムの再起動の間で永続化します。  
  
|||||  
|-|-|-|-|  
|列名|データ型|Description|範囲|  
|run_id|**int**|実行のローダーの一意の識別子。||  
|ステージ|**nvarchar (30)**|実行の現在のステージです。|'CREATE_STAGING'、'DMS_LOAD'、'LOAD_INSERT'、'LOAD_CLEANUP'|  
|request_id|**nvarchar (32)**|この段階を実行している要求の ID。||  
|ステータス|**nvarchar (16)**|このフェーズの状態です。||  
|start_time|**datetime**|ステージの開始時刻。||  
|end_time|**datetime**|時間は、ステージの終了時刻、存在する場合です。|開始されていない場合、または進行状況では NULL です。|  
|total_elapsed_time|**int**|この段階で費やされた (またはこれまでに費やされた) の合計時間が実行されています。|Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超えるをオーバーフローしました期日の実体化エラーが発生します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
