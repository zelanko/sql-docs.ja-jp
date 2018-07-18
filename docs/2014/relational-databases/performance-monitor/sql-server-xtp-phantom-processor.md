---
title: XTP Phantom Processor |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
caps.latest.revision: 4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1218f92622f9294c15afe417bcebbe84ad0df5da
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175879"
---
# <a name="xtp-phantom-processor"></a>XTP Phantom Processor
  XTP Phantom Processor パフォーマンス オブジェクトには、XTP エンジンのファントム処理サブシステムに関連するカウンターが含まれています。 このコンポーネントには、SERIALIZABLE 分離レベルで実行されているトランザクション内のファントム行を検出する役割があります。  
  
 この表は、 **XTP Phantom Processor**カウンター。  
  
|カウンター|説明|  
|-------------|-----------------|  
|**Dusty corner scan retries/sec (Phantom-issued)**|ファントム プロセッサによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。 これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。|  
|**Phantom expired rows removed/sec**|ファントム スキャンによって削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Phantom expired rows touched/sec**|ファントム スキャンによって操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Phantom expiring rows touched/sec**|ファントム スキャンによって操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。|  
|**Phantom rows touched/sec**|ファントム スキャンによって操作された行の数に関する 1 秒あたりの平均です。|  
|**Phantom scans started/sec**|ファントム スキャンが開始された回数に関する 1 秒あたりの平均です。|  
  
## <a name="see-also"></a>参照  
 [XTP &#40;、インメモリ OLTP&#41;パフォーマンス カウンター](../../integration-services/performance/performance-counters.md)  
  
  
