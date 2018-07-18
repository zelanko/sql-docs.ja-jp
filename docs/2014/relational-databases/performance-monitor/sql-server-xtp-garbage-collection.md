---
title: XTP Garbage Collection |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c2a968f1fa15f0f61d988f5068ab5ce39be0808e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299938"
---
# <a name="xtp-garbage-collection"></a>XTP Garbage Collection
  XTP Garbage Collection パフォーマンス オブジェクトには、XTP エンジンのガベージ コレクターに関連するカウンターが含まれています。  
  
 この表は、 **XTP garbage Collection**カウンター。  
  
|カウンター|説明|  
|-------------|-----------------|  
|**Dusty corner scan retries/sec (GC-issued)**|ガベージ コレクターによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。 これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。|  
|**Main GC work items/sec**|メイン GC スレッドで処理された作業項目の数です。|  
|**Parallel GC work item/sec**|並列スレッドが GC 作業項目を実行した回数です。|  
|**Rows processed/sec**|ガベージ コレクターにより 1 秒間に処理された (平均) 行数です。|  
|**Rows processed/sec (first in bucket and removed)**|ガベージ コレクターによって処理され、最初は対応するハッシュ バケット内に存在し、直ちに削除することができた行の数に関する 1 秒あたりの平均です。|  
|**Rows processed/sec (first in bucket)**|ガベージ コレクターによって処理され、最初は対応するハッシュ バケット内に存在していた行の数に関する 1 秒あたりの平均です。|  
|**Rows processed/sec (marked for unlink)**|ガベージ コレクターによって処理され、既にリンク解除のマークが付いていた行の数に関する 1 秒あたりの平均です。|  
|**Rows processed/sec (no sweep needed)**|ガベージ コレクターによって処理され、ダスティ コーナー スウィープ (詳細なクリーンアップ) を必要としない行の数に関する 1 秒あたりの平均です。|  
|**Sweep expired rows removed/sec**|ダスティ コーナー スウィープの実行中に削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Sweep expired rows touched/sec**|ダスティ コーナー スウィープの実行中に操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Sweep expiring rows touched/sec**|ダスティ コーナー スウィープの実行中に操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。|  
|**Sweep rows touched/sec**|ダスティ コーナー スウィープの実行中に操作された行の数に関する 1 秒あたりの平均です。|  
|**Sweep scans started/sec**|ダスティ コーナー スウィープ スキャンが開始された回数に関する 1 秒あたりの平均。|  
  
## <a name="see-also"></a>参照  
 [XTP &#40;、インメモリ OLTP&#41;パフォーマンス カウンター](../../integration-services/performance/performance-counters.md)  
  
  
