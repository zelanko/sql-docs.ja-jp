---
title: 変更追跡関数 (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
caps.latest.revision: 10
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c478d4ca59db55cefe5e13444fd81ea7bf64dbea
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "33227267"
---
# <a name="change-tracking-functions-transact-sql"></a>変更追跡関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  変更の追跡は、追跡対象のテーブルに対して適用された挿入、更新、削除の各アクティビティを記録し、変更の詳細を利用しやすいリレーショナル形式で格納します。 次の関数は、変更に関する情報を返します。  
  
|機能|説明|  
|--------------|-----------------|  
|[CHANGETABLE (CHANGES)](../../relational-databases/system-functions/changetable-transact-sql.md)|指定したバージョン以降にテーブルに対して行われたすべての変更の追跡情報を返します。|  
|[CHANGETABLE (VERSION)](../../relational-databases/system-functions/changetable-transact-sql.md)|指定した行に関する最新の変更追跡情報を返します。|  
|[CHANGE_TRACKING_MIN_VALID_VERSION()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|変更の追跡を使用しているときの指定したテーブルから情報を取得するに使用するための有効な最小バージョンを返します、 [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md)関数。|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|最後にコミットされたトランザクションに関連付けられているバージョンを取得します。 次に CHANGETABLE を使用して変更を列挙するとき、このバージョンを使用できます。|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|CHANGETABLE(CHANGES ...) 関数によって返される SYS_CHANGE_COLUMNS 値を解釈します。|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|アプリケーションにおけるデータ変更時の、実行者 ID などの変更コンテキストの指定を有効化します。|  
  
## <a name="see-also"></a>参照  
 [データ変更の追跡 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
