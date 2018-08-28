---
title: PreConnect:Starting イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e040b5676b6e620705c076e1174f16f93b7d02b4
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43073303"
---
# <a name="preconnectstarting-event-class"></a>PreConnect:Starting イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  PreConnect:Starting イベント クラスは、LOGON トリガーまたはリソース ガバナーの分類関数が実行を開始したことを示します。  
  
## <a name="preconnectstarting-event-class-data-columns"></a>PreConnect:Starting イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|215|27|いいえ|  
|SPID|**int**|このイベントを発生させるサーバー プロセスの ID。|12|[ユーザー アカウント制御]|  
|EventSubClass|**int**|ユーザー定義の分類子関数の場合は 1。|21|[ユーザー アカウント制御]|  
|StartTime|**datetime**|ユーザー定義の分類子関数が開始された時刻。|14|[ユーザー アカウント制御]|  
|ObjectID|**int**|ユーザー定義の分類オブジェクトの ID。|22|[ユーザー アカウント制御]|  
|ObjectName|**nvarchar (256)**|ユーザー定義の分類子関数の 2 部構成の名前 (dbo.classifier など)。|34|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Completed イベント クラス](../../relational-databases/event-classes/preconnect-completed-event-class.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  
