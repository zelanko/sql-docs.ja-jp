---
description: pdw_loader_run_stages (Transact-sql)
title: pdw_loader_run_stages (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b2af896ec6a187f81c523ee172662141b71cffb8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88377008"
---
# <a name="syspdw_loader_run_stages-transact-sql"></a>pdw_loader_run_stages (Transact-sql)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  で実行中および完了した読み込み操作に関する情報を格納 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] します。 情報は、システムの再起動の間で永続化します。  
  
| 列名 | データ型 | 説明 | Range |
| ----------- | --------- | ----------- | ----- |
|run_id|**int**|ローダー実行の一意識別子。||  
|準備|**nvarchar(30)**|実行の現在のステージ。|' CREATE_STAGING '、' DMS_LOAD '、' LOAD_INSERT '、' LOAD_CLEANUP '|  
|request_id|**nvarchar(32)**|このステージを実行している要求の ID。||  
|status|**nvarchar (16)**|このフェーズの状態。||  
|start_time|**datetime**|ステージが開始された時刻。||  
|end_time|**datetime**|ステージが終了した時刻 (存在する場合)。|開始されていないか処理中の場合は NULL です。|  
|total_elapsed_time|**int**|このステージの実行にかかった合計時間 (またはこれまでに費やされた時間)。|Total_elapsed_time が整数の最大値 (ミリ秒単位で24.8 日) を超えた場合、オーバーフローによる具体化エラーが発生します。<br /><br /> ミリ秒単位の最大値は24.8 日に相当します。|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
