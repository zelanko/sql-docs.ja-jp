---
title: XTP トランザクション |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 443d67e4-1c7f-41d7-b18d-2d657f58c22a
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6b890ec229755db9c6ee9b292bf632d110e9c189
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077507"
---
# <a name="xtp-transactions"></a>XTP Transactions
  XTP Transactions パフォーマンス オブジェクトには、XTP エンジン トランザクションに関連するカウンターが含まれています。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 この表は、 **XTP トランザクション**カウンターです。  
  
|カウンター|説明|  
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
 [XTP &#40;、インメモリ OLTP&#41;パフォーマンス カウンター](../../integration-services/performance/performance-counters.md)  
  
  