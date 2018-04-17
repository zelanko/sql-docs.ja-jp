---
title: dbo.sysdownloadlist (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysdownloadlist
- sysdownloadlist_TSQL
- dbo.sysdownloadlist_TSQL
- sysdownloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sysdownloadlist system table
ms.assetid: 71087a4c-e829-488e-aa7d-a9476e2b4779
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 77e6f3c548e7ab610b84c68cc1545836cfc02c77
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべての対象サーバーに対するダウンロード命令のキューを格納します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|行の挿入順序を表す ID 列。|  
|**source_server**|**sysname**|ソース サーバーの名前。|  
|**operation_code**|**tinyint**|ジョブの操作コード。<br /><br /> **1**アドイン (INSERT) を =<br /><br /> **2** UPD (更新) を =<br /><br /> **3** DEL (削除) を =<br /><br /> **4**開始を =<br /><br /> **5**停止を =|  
|**object_type**|**tinyint**|オブジェクトの種類のコード。|  
|**object_id** <sup>1</sup>|**uniqueidentifier**|オブジェクト ID 番号。|  
|**target_server**|**sysname**|対象サーバーの名前。|  
|**error_message**|**nvarchar(1024)**|対象サーバーが特定の行を処理しているときにエラーが発生した場合のエラー メッセージ。|  
|**date_posted**|**datetime**|ジョブが対象サーバーに通知された日付と時刻。|  
|**date_downloaded**|**datetime**|ジョブが前回ダウンロードされた日付と時刻。|  
|**ステータス**|**tinyint**|ジョブのステータス。<br /><br /> **0** = 未ダウンロード<br /><br /> **1** = 正常にダウンロード|  
|**deleted_object_name**|**sysname**|削除されたオブジェクトの名前。|  
  
 <sup>1</sup> 、 **object_id**列の値にすることができます**-1**、場合、すべての値に対応する、 **operation_code**列は削除の値。  
  
  
