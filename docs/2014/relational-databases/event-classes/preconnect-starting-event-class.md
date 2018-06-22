---
title: PreConnect:Starting イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ae1972bde3d0d13a608f4583e88e2b649ab82be3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076228"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting イベント クラス
  PreConnect:Starting イベント クラスは、LOGON トリガーまたはリソース ガバナーの分類関数が実行を開始したことを示します。  
  
## <a name="preconnectstarting-event-class-data-columns"></a>PreConnect:Starting イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|215|27|いいえ|  
|SPID|`int`|このイベントを発生させるサーバー プロセスの ID。|12|はい|  
|EventSubClass|`int`|ユーザー定義の分類子関数の場合は 1。|21|はい|  
|StartTime|`datetime`|ユーザー定義の分類子関数が開始された時刻。|14|はい|  
|ObjectID|`int`|ユーザー定義の分類オブジェクトの ID。|22|はい|  
|ObjectName|`nvarchar(256)`|ユーザー定義の分類子関数の 2 部構成の名前 (dbo.classifier など)。|34|はい|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../extended-events/extended-events.md)   
 [PreConnect:Completed イベント クラス](preconnect-completed-event-class.md)   
 [リソース ガバナー](../resource-governor/resource-governor.md)  
  
  