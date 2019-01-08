---
title: 変更追跡関数 (TRANSACT-SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], change tracking
- change tracking [SQL Server], functions
ms.assetid: 04eb53c4-8b69-414e-9696-185d227fea35
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dcd12d2495c0be6ec3a643b5c5f0f34d2e50f156
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52544385"
---
# <a name="change-tracking-functions-transact-sql"></a>変更追跡関数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  変更の追跡は、追跡対象のテーブルに対して適用された挿入、更新、削除の各アクティビティを記録し、変更の詳細を利用しやすいリレーショナル形式で格納します。 次の関数は、変更に関する情報を返します。  
  
|関数|説明|  
|--------------|-----------------|  
|[CHANGETABLE (CHANGES)](../../relational-databases/system-functions/changetable-transact-sql.md)|指定したバージョン以降にテーブルに対して行われたすべての変更の追跡情報を返します。|  
|[CHANGETABLE (VERSION)](../../relational-databases/system-functions/changetable-transact-sql.md)|指定した行に関する最新の変更追跡情報を返します。|  
|[CHANGE_TRACKING_MIN_VALID_VERSION()](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)|変更を使用しているときに、指定したテーブルから追跡情報を取得するに使用するために有効な最小バージョンを返します、 [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md)関数。|  
|[CHANGE_TRACKING_CURRENT_VERSION](../../relational-databases/system-functions/change-tracking-current-version-transact-sql.md)|最後にコミットされたトランザクションに関連付けられているバージョンを取得します。 次に CHANGETABLE を使用して変更を列挙するときのこのバージョンを使用することができます。|  
|[CHANGE_TRACKING_IS_COLUMN_IN_MASK](../../relational-databases/system-functions/change-tracking-is-column-in-mask-transact-sql.md)|CHANGETABLE(CHANGES...) 関数によって返される SYS_CHANGE_COLUMNS 値を解釈します。|  
|[WITH CHANGE_TRACKING_CONTEXT](../../relational-databases/system-functions/with-change-tracking-context-transact-sql.md)|アプリケーションにおけるデータ変更時の、実行者 ID などの変更コンテキストの指定を有効化します。|  
  
## <a name="see-also"></a>参照  
 [データ変更の追跡 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
