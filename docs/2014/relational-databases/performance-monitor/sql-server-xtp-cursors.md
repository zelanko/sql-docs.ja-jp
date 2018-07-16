---
title: XTP Cursors |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
caps.latest.revision: 4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c5eab11a0ee57a8545a2d19f8a7472392635e690
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37206982"
---
# <a name="xtp-cursors"></a>XTP Cursors
  XTP Cursors パフォーマンス オブジェクトには、XTP エンジンの内部カーソルに関連するカウンターが含まれています。 カーソルは、低レベルの構成の処理に XTP エンジンの使用をブロックする[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ。 このため、通常はユーザー側でカーソルを直接管理することはありません。  
  
 この表は、 **XTP Cursors**カウンター。  
  
|カウンター|説明|  
|-------------|-----------------|  
|**Cursor deletes/sec**|カーソルの削除回数に関する 1 秒あたりの平均です。|  
|**Cursor inserts/sec**|カーソルの挿入回数に関する 1 秒あたりの平均です。|  
|**Cursor scans started /sec**|カーソル スキャンが開始された回数に関する 1 秒あたりの平均です。|  
|**Cursor unique violations/sec**|UNIQUE 制約の違反に関する 1 秒あたりの平均です。|  
|**Cursor updates/sec**|カーソルの更新回数に関する 1 秒あたりの平均です。|  
|**Cursor write conflicts/sec**|同じ行バージョンに対する書き込み - 書き込みの競合回数に関する 1 秒あたりの平均です。|  
|**Dusty corner scan retries/sec (user-issued)**|ユーザーのフル テーブル スキャンによって発行されたダスティ コーナー スウィープ (詳細なクリーンアップ) の実行中に、書き込みの競合が原因で発生したスキャン再試行回数に関する 1 秒あたりの平均です。 これは非常に低レベルのカウンターであり、お客様による使用は想定されていません。|  
|**Expired rows removed/sec**|カーソルによって削除された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Expired rows touched/sec**|カーソルによって操作された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Rows returned/sec**|カーソルによって返された、有効期限切れの行の数に関する 1 秒あたりの平均です。|  
|**Rows touched/sec**|カーソルによって操作された行の数に関する 1 秒あたりの平均です。|  
|**Tentatively-deleted rows touched/sec**|カーソルによって操作された、間もなく期限切れになる行の数に関する 1 秒あたりの平均です。 行が間もなく期限切れになるのは、その行を削除したトランザクションが依然としてアクティブな場合 (つまり、コミットや中止がまだ行われていない場合) です。|  
  
## <a name="see-also"></a>参照  
 [XTP &#40;、インメモリ OLTP&#41;パフォーマンス カウンター](../../integration-services/performance/performance-counters.md)  
  
  
