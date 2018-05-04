---
title: sys.dm_xe_objects (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_xe_objects
- sys.dm_xe_objects
- sys.dm_xe_objects_TSQL
- dm_xe_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_objects dynamic management view
- extended events [SQL Server], views
ms.assetid: 5d944b99-b097-491b-8cbd-b0e42b459ec0
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f9f317555f992261eb76d65dae4e7d0e91163f71
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmxeobjects-transact-sql"></a>sys.dm_xe_objects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  イベント パッケージによって公開されるオブジェクトごとに 1 行のデータを返します。 オブジェクトは、次のいずれかです。  
  
-   イベント。 イベントは、実行パスにおける対象のポイントを示します。 すべてのイベントには、対象のポイントに関する情報が含まれます。  
  
-   アクション。 アクションは、イベントの発生に同期して実行されます。 アクションを使用して、実行時データをイベントに追加することもできます。  
  
-   ターゲット。 ターゲットは、イベントを開始したスレッド上で同期的にまたはシステムによって提供されたスレッド上で非同期的に、イベントを使用します。  
  
-   述語。 述語ソースは、比較演算で使用する値をイベント ソースから取得します。 述語の比較では、特定のデータ型が比較され、ブール値が返されます。  
  
-   型。 型は、データを解釈するために必要なバイト コレクションの長さと特性をカプセル化します。  

 |列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(60)**|オブジェクトの名前。 名前は、特定のオブジェクトの種類のパッケージ内で一意です。 NULL 値は許可されません。|  
|object_type|**nvarchar(60)**|オブジェクトの古い型。 object_type では、次のいずれかです。<br /><br /> イベント<br /><br /> アクション (action)<br /><br /> ターゲット (target)<br /><br /> pred_source<br /><br /> pred_compare<br /><br /> 型<br /><br /> NULL 値は許可されません。|  
|package_guid|**uniqueidentifier**|このアクションを公開するパッケージの GUID。 sys.dm_xe_packages.package_id との間に多対一のリレーションシップがあります。 NULL 値は許可されません。|  
|description|**nvarchar (256)**|アクションの説明です。 説明については、パッケージの作成者によって設定されます。 NULL 値は許可されません。|  
|capabilities|**int**|オブジェクトの機能を表すビットマップ。 NULL 値が許可されます。|  
|capabilities_desc|**nvarchar (256)**|オブジェクトのすべての機能を一覧表示します。 NULL 値が許可されます。<br /><br /> **すべてのオブジェクトの種類に適用される機能**<br /><br /> —<br />                                **プライベート**です。 内部的に使用できる唯一のオブジェクトであり、CREATE/ALTER EVENT SESSION DDL ではアクセスできません。 内部的に使用される少数のオブジェクトに加えて、監査イベントとターゲットがこのカテゴリに含まれます。<br /><br /> ===============<br /><br /> **イベント機能**<br /><br /> —<br />                                **No_block**です。 イベントは、どのような理由でもブロックできない重要なコード パス内にあります。 この機能を持つイベントは、NO_EVENT_LOSS が指定されているイベント セッションには追加できません。<br /><br /> ===============<br /><br /> **すべてのオブジェクトの種類に適用される機能**<br /><br /> —<br />                                **Process_whole_buffers**です。 ターゲットは、イベントごとではなく、イベントのバッファーをまとめて使用します。<br /><br /> —<br />                        **シングルトン**です。 プロセスにはターゲットのインスタンスが 1 つだけ存在できます。 複数のイベント セッションで同じシングルトン ターゲットを参照できますが、インスタンスは 1 つだけであり、そのインスタンスが一意の各イベントを 1 回だけ認識します。 これは、すべてが同じイベントを収集する複数のセッションにターゲットが追加される場合に重要です。<br /><br /> —<br />                                **Synchronous**。 ターゲットは、イベントを生成しているスレッドで、制御が呼び出し元のコード行に返される前に実行されます。|  
|type_name|**nvarchar(60)**|pred_source オブジェクトおよび pred_compare オブジェクトの名前。 NULL 値が許可されます。|  
|type_package_guid|**uniqueidentifier**|このオブジェクトの対象となる型を公開するパッケージの GUID。 NULL 値が許可されます。|  
|type_size|**int**|データ型のサイズ (バイト単位)。 有効なオブジェクト型に対してのみ使用できます。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
### <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_xe_objects.package_guid|sys.dm_xe_packages.guid|多対一|  
  
## <a name="see-also"></a>参照  
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

