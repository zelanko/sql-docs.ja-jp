---
title: SQL Server XTP IO ガバナー | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c5c66968245ff2944d1d16e73ed766b7e09ef122
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158540"
---
# <a name="sql-server-xtp-io-governor"></a>SQL Server XTP IO ガバナー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server XTP IO ガバナーのパフォーマンス オブジェクトには、インメモリ OLTP IO レート ガバナーに関連するカウンターが含まれています。

次の表で、 **SQL Server XTP IO ガバナー** カウンターについて説明します。

|カウンター|[説明]|  
|-------------|-----------------|  
|**1 秒あたりの不十分なクレジット待機数**|レート オブジェクトのクレジット不足に起因する待機数 (1 秒あたり)。|
|**1 秒あたりに発行された Io 数**|フラッシュ スレッドにより発行された Io 数 (1 秒あたり)。|
|**1 秒あたりのログ ブロック数**|コントローラーによって処理されたログ ブロック数 (1 秒あたり)。|
|**実行されなかったクレジット スロット数**|レート オブジェクトからのクレジットを待ったために実行されなかったクレジット スロット数。|
|**1 秒あたりの古いレート オブジェクト待機数**|古いレート オブジェクトに起因する待機数 (1 秒あたり)。|
|**公開されたレート オブジェクトの合計**|公開されたレート オブジェクトの合計数。|
 

## <a name="see-also"></a>参照  
[SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
