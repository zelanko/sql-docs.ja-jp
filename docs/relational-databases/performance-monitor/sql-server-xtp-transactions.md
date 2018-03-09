---
title: "SQL Server XTP トランザクション | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a618d481201cdc0bbb764e5551a035ab609ccb24
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="sql-server-xtp-transactions"></a>SQL Server XTP トランザクション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP トランザクション ログ パフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインメモリ OLTP を含むトランザクション に関連するカウンターが含まれています。  
  
 次の表では、 **SQL Server XTP トランザクション** のカウンターについて説明します。  
  
|カウンター|Description|  
|-------------|-----------------|  
|**Cascading aborts/sec**|コミット依存ロールバックが原因でロールバックされたトランザクション数に関する 1 秒あたりの平均です。|  
|**Commit dependencies taken/sec**|トランザクションにより処理されたコミット依存の数に関する 1 秒間の平均です。|  
|**Read-only transactions prepared/sec**|コミット処理の目的で準備された読み取り専用トランザクションの数に関する 1 秒あたりの値です。|  
|**Save point refreshes/sec**|セーブポイントが "更新" された回数に関する 1 秒あたりの平均です。 セーブポイントの更新が発生するのは、既存のセーブポイントを、トランザクションの有効期間内での現在の状態にリセットしたときです。|  
|**Save point rollbacks/sec**|トランザクションがセーブポイントまでロールバックされた回数に関する 1 秒あたりの平均です。|  
|**Save points created /sec**|セーブポイントが作成された回数に関する 1 秒あたりの平均です。|  
|**Transaction validation failure/sec**|トランザクションが検証処理に失敗した回数に関する 1 秒間の平均です。|  
|**Transactions aborted by user/sec**|トランザクションがユーザーによって中止された回数に関する 1 秒間の平均です。|  
|**Transactions aborted/sec**|トランザクションが (ユーザーとシステムの両方によって) 中止された回数に関する 1 秒間の平均です。|  
|**Transactions created/sec**|システム内でトランザクションが作成された回数に関する 1 秒間の平均です。<br /><br /> XTP トランザクションは、ディスク ベース トランザクションとは別にカウントされます (Databases:Transactions/sec に反映)。 たとえば、読み取り専用トランザクションは Transactions created/sec でカウントされますが、Databases:Transactions/sec ではカウントされません。|  
  
## <a name="see-also"></a>参照  
 [SQL Server XTP &#40;インメモリ OLTP&#41; パフォーマンス カウンター](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
