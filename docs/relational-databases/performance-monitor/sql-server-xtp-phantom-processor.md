---
title: SQL Server XTP Phantom Processor | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 722137db4fdddd79f8ed4bfe8d5a7c3ed4531738
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-xtp-phantom-processor"></a>SQL Server XTP Phantom Processor
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP Phantom Processor パフォーマンス オブジェクトには、インメモリ OLTP エンジンのファントム処理サブシステムに関連するカウンターが含まれています。 このコンポーネントには、同時実行シナリオの制約検証の他に、SERIALIZABLE 分離レベルで実行されているトランザクション内のファントム行を検出する役割があります。  
  
 次の表では、 **SQL Server Phantom Processor** カウンターについて説明します。  
  
|カウンター|説明|  
|-------------|-----------------|  
|**Dusty corner scan retries/sec (Phantom-issued)**|ファントム プロセッサによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。 これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。|  
|**Phantom expired rows removed/sec**|ファントム スキャンによって削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Phantom expired rows touched/sec**|ファントム スキャンによって操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Phantom expiring rows touched/sec**|ファントム スキャンによって操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。|  
|**Phantom rows touched/sec**|ファントム スキャンによって操作された行の数に関する 1 秒あたりの平均です。|  
|**Phantom scans started/sec**|ファントム スキャンが開始された回数に関する 1 秒あたりの平均です。|  
  
## <a name="see-also"></a>参照  
 [SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
