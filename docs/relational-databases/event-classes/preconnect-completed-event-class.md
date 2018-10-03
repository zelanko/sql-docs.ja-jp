---
title: PreConnect:Completed イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3d44fd5f6e0d2196af84f890fcbc591e10c036f6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690560"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  PreConnect:Completed イベント クラスは、LOGON トリガーまたはリソース ガバナー分類関数の実行が終了したことを示します。  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>PreConnect:Completed イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|いいえ|  
|SPID|**int**|このイベントを発生させるサーバー プロセスの ID。|12|[ユーザー アカウント制御]|  
|EventSubClass|**int**|ユーザー定義の分類子関数の場合は 1。|21|[ユーザー アカウント制御]|  
|StartTime|**datetime**|ユーザー定義の分類子関数が開始された時刻。|14|[ユーザー アカウント制御]|  
|EndTime|**datetime**|ユーザー定義の分類子関数が開始された時刻。|15|[ユーザー アカウント制御]|  
|Duration|**bigint**|分類子関数によって使用された時間 (マイクロ秒)。|13|[ユーザー アカウント制御]|  
|ObjectID|**int**|ユーザー定義の分類オブジェクトの ID。|22|[ユーザー アカウント制御]|  
|CPU|**int**|CPU 使用率 (ミリ秒単位)。|18|[ユーザー アカウント制御]|  
|Reads|**int**|論理読み取りの数。|16|[ユーザー アカウント制御]|  
|Writes|**int**|論理書き込みの数。|17|[ユーザー アカウント制御]|  
|GroupID|**int**|分類されたワークロード グループの ID。|66|[ユーザー アカウント制御]|  
|[エラー]|**int**|ユーザー定義の分類子関数が実行に失敗した場合の最後のエラー番号。|31|[ユーザー アカウント制御]|  
|状態|**int**|最後のエラーの状態。|30|[ユーザー アカウント制御]|  
|TargetUserName|**sysname**|対応するアクティブなグループをシステムが見つけられない場合は、ユーザー定義の分類子関数の戻り値 (ワークロード グループ名)。 それ以外の場合は、この列は NULL に設定されます。|39|[ユーザー アカウント制御]|  
|ObjectName|**nvarchar (256)**|ユーザー定義の分類子関数の 2 部構成の名前 (dbo.classifier など)。|34|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting イベント クラス](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  
