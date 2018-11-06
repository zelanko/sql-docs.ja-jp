---
title: SQL Server XTP Phantom Processor | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance-monitor
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ae89a3572c0c9cc4a3329deb85a34eee16c869b6
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "51030521"
---
# <a name="sql-server-xtp-phantom-processor"></a>SQL Server XTP Phantom Processor
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP Phantom Processor パフォーマンス オブジェクトには、インメモリ OLTP エンジンのファントム処理サブシステムに関連するカウンターが含まれています。 このコンポーネントには、コンカレンシー シナリオの制約検証の他に、SERIALIZABLE 分離レベルで実行されているトランザクション内のファントム行を検出する役割があります。  
  
 次の表では、 **SQL Server Phantom Processor** カウンターについて説明します。  
  
|カウンター|[説明]|  
|-------------|-----------------|  
|**Dusty corner scan retries/sec (Phantom-issued)**|ファントム プロセッサによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。 これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。|  
|**Phantom expired rows removed/sec**|ファントム スキャンによって削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Phantom expired rows touched/sec**|ファントム スキャンによって操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Phantom expiring rows touched/sec**|ファントム スキャンによって操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。|  
|**Phantom rows touched/sec**|ファントム スキャンによって操作された行の数に関する 1 秒あたりの平均です。|  
|**Phantom scans started/sec**|ファントム スキャンが開始された回数に関する 1 秒あたりの平均です。|  
  
## <a name="see-also"></a>参照  
 [SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
