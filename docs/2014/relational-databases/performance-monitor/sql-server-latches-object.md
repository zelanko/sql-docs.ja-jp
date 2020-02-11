---
title: SQL Server の Latches オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Latches object
- SQLServer:Latches
ms.assetid: 2393ea1c-2bf3-41c3-9f37-b9761144eeca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a6d0d9249a5cfb801e07a85132060bb4d1781346
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63251100"
---
# <a name="sql-server-latches-object"></a>SQL Server の Latches オブジェクト
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**SQLServer: ラッチ**オブジェクトには、ラッチと呼ば[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]れる内部リソースロックを監視するためのカウンターが用意されています。 ユーザーの利用状況とリソース使用率を調べるために行うラッチの監視は、パフォーマンスのボトルネックを特定するために役立つことがあります。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Latches** カウンターについて説明します。  
  
|SQL Server Latches カウンター|[説明]|  
|---------------------------------|-----------------|  
|**ラッチの平均待機時間 (ミリ秒)**|待機しなければならなかったラッチ要求の平均ラッチ待ち時間 (ミリ秒)。|  
|**ラッチ待機数/秒**|直ちに許可できなかったラッチ要求の数。|  
|**スーパーラッチの数**|現在の SuperLatch であるラッチの数。|  
|**SuperLatch の降格/秒**|最後の 1 秒間に通常のラッチに降格された SuperLatch の数。|  
|**SuperLatch の昇格数/秒**|最後の 1 秒間に SuperLatch に昇格されたラッチの数。|  
|**ラッチの合計待機時間 (ミリ秒)**|直前のラッチ要求の合計ラッチ待ち時間 (ミリ秒)。|  
  
## <a name="see-also"></a>参照  
 [リソース使用状況の監視 &#40;システムモニタ&#41;](monitor-resource-usage-system-monitor.md)  
  
  
