---
title: sys.database_event_session_targets (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 38d775ee-1fe1-4820-88c6-02b2f875a66b
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8828532142bbcd8c188286ba87c16c3b824a279c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62751541"
---
# <a name="sysdatabaseeventsessiontargets-azure-sql-database"></a>sys.database_event_session_targets (Azure SQL Database)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  イベント セッションのイベント ターゲットごとに 1 行のデータを返します。  
  
||  
|-|  
|**適用対象**:[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のバージョン。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベント セッションの ID。 NULL 値は許可されません。|  
|target_id|**int**|ターゲットの ID。 ID、イベント セッション オブジェクト内で一意です。 NULL 値は許可されません。|  
|NAME|**sysname**|イベント ターゲットの名前。 NULL 値は許可されません。|  
|パッケージ (package)|**sysname**|イベント ターゲットを含むイベント パッケージの名前。 NULL 値は許可されません。|  
|モジュール|**sysname**|イベント ターゲットを含むモジュールの名前。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 このビューには、次のリレーションシップの基数があります。  
  
||||  
|-|-|-|  
|From|変換先|リレーションシップ|  
|sys.database_event_session_targets.event_session_id|sys.database_event_sessions.event_session_id|多対一|  
  
## <a name="see-also"></a>関連項目  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
