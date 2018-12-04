---
title: SQL Server XTP トランザクション | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 46a0f7cb314cf072dbed8d421e55bb2f2648c611
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158820"
---
# <a name="sql-server-xtp-transactions"></a>SQL Server XTP トランザクション
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP トランザクション ログ パフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインメモリ OLTP を含むトランザクション に関連するカウンターが含まれています。  
  
 次の表では、 **SQL Server XTP トランザクション** のカウンターについて説明します。  
  
|カウンター|[説明]|  
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
  
  
