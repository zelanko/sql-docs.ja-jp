---
title: SQL Server の ExecStatistics オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 40057a96100013c413b0f2a02c0abb44d4f26675
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030291"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server の ExecStatistics オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Microsoft SQL Server の **SQLServer:ExecStatistics** オブジェクトには、さまざまな実行を監視するためのカウンターがあります。  
  
 次の表では、SQL Server の **Exec Statistics** カウンターについて説明します。  
  
|SQL Server Exec Statistics のカウンター|[説明]|  
|-----------------------------------------|-----------------|  
|**Distributed Query**|分散クエリの実行に関連する統計データ。|  
|**DTC calls**|DTC 呼び出しの実行に関連する統計データ。|  
|**Extended Procedures**|拡張プロシージャの実行に関連する統計データ。|  
|**OLEDB calls**|OLEDB 呼び出しの実行に関連する統計データ。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|アイテム|[説明]|  
|----------|-----------------|  
|**Average execution time (ms)**|選択した種類の実行の平均実行時間。|  
|**Cumulative execution time (ms) per second**|選択した種類の実行の 1 秒あたりの累積実行時間。|  
|**Execs in progress**|選択した種類の実行のうち現在進行中の数。|  
|**Exec started per second**|選択した種類の実行が 1 秒あたりに開始される数。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
