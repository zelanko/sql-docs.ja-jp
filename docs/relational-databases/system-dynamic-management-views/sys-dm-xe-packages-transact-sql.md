---
title: sys.dm_xe_packages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_xe_packages_TSQL
- sys.dm_xe_packages_TSQL
- dm_xe_packages
- sys.dm_xe_packages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_packages dynamic management view
- extended events [SQL Server], views
ms.assetid: 2e5ecbe9-3ea8-45e6-a161-e31671a03e1d
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1be7763fbbf1e2f530d3e9d8530278d461bdfc13
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmxepackages-transact-sql"></a>sys.dm_xe_packages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  拡張イベント エンジンに登録されているすべてのパッケージを一覧表示します。  
  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(60)**|パッケージの名前。 説明は、パッケージ自体から公開されます。 NULL 値は許可されません。|  
|guid|**uniqueidentifier**|パッケージを識別する GUID。 NULL 値は許可されません。|  
|description|**nvarchar (256)**|パッケージの説明。 descriptionis では、パッケージの作成者によって設定され、null 値を許容することはできません。|  
|capabilities|**int**|このパッケージの機能を説明するビットマップ。 NULL 値が許可されます。|  
|capabilities_desc|**nvarchar (256)**|このパッケージで使用できるすべての機能の一覧。 NULL 値が許可されます。|  
|module_guid|**uniqueidentifier**|このパッケージを公開するモジュールの GUID。 NULL 値は許可されません。|  
|module_address|**varbinary(8)**|パッケージを含むモジュールが読み込まれるベース アドレス。 1 つのモジュールで複数のパッケージが公開される場合があります。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 拡張イベント エンジンに登録されているパッケージでは、イベント、イベントの発生時に実行できるアクション、およびイベント データの同期処理および非同期処理の対象が公開されます。  
  
 これらのパッケージは、プロセスのアドレス空間に動的に読み込むことができます。 パッケージの読み込み時、パッケージが公開するすべてのオブジェクトが拡張イベント エンジンに登録されます。  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
||||  
|-|-|-|  
|From|変換先|リレーションシップ|  
|sys.dm_xe_packages.module_address|sys.dm_os_loaded_modules.base_address|多対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

