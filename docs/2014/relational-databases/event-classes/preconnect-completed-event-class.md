---
title: PreConnect:Completed イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 16720db613815d5c8cce501c1cee2d5d3cc9b3cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48150632"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed イベント クラス
  PreConnect:Completed イベント クラスは、LOGON トリガーまたはリソース ガバナー分類関数の実行が終了したことを示します。  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>PreConnect:Completed イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|いいえ|  
|SPID|`int`|このイベントを発生させるサーバー プロセスの ID。|12|はい|  
|EventSubClass|`int`|ユーザー定義の分類子関数の場合は 1。|21|はい|  
|StartTime|`datetime`|ユーザー定義の分類子関数が開始された時刻。|14|はい|  
|EndTime|`datetime`|ユーザー定義の分類子関数が開始された時刻。|15|はい|  
|Duration|`bigint`|分類子関数によって使用された時間 (マイクロ秒)。|13|はい|  
|ObjectID|`int`|ユーザー定義の分類オブジェクトの ID。|22|はい|  
|CPU|`int`|CPU 使用率 (ミリ秒単位)。|18|はい|  
|Reads|`int`|論理読み取りの数。|16|はい|  
|Writes|`int`|論理書き込みの数。|17|はい|  
|GroupID|`int`|分類されたワークロード グループの ID。|66|はい|  
|[エラー]|`int`|ユーザー定義の分類子関数が実行に失敗した場合の最後のエラー番号。|31|はい|  
|状態|`int`|最後のエラーの状態。|30|はい|  
|TargetUserName|`sysname`|対応するアクティブなグループをシステムが見つけられない場合は、ユーザー定義の分類子関数の戻り値 (ワークロード グループ名)。 それ以外の場合は、この列は NULL に設定されます。|39|はい|  
|ObjectName|`nvarchar(256)`|ユーザー定義の分類子関数の 2 部構成の名前 (dbo.classifier など)。|34|はい|  
  
## <a name="see-also"></a>関連項目  
 [拡張イベント](../extended-events/extended-events.md)   
 [PreConnect:Starting イベント クラス](preconnect-starting-event-class.md)   
 [リソース ガバナー](../resource-governor/resource-governor.md)  
  
  
