---
title: sysdownloadlist (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03e888cc3d36b909035247d5f1c16dd1ab61e0d3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061194"
---
# <a name="dbosysdownloadlist-transact-sql"></a>dbo.sysdownloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  すべてのターゲット サーバーに対するダウンロード命令のキューを格納します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|行の自然な挿入シーケンスを提供する id 列。|  
|**source_server**|**sysname**|ソース サーバーの名前。|  
|**operation_code**|**tinyint**|ジョブの操作コード:<br /><br /> **1** = INS (挿入)<br /><br /> **2** = UPD (更新)<br /><br /> **3** = DEL (delete)<br /><br /> **4** = 開始<br /><br /> **5** = 停止|  
|**object_type**|**tinyint**|オブジェクトの種類のコード。|  
|**object_id** <sup>1</sup>|**UNIQUEIDENTIFIER**|オブジェクト ID 番号。|  
|**target_server**|**sysname**|対象サーバーの名前。|  
|**error_message**|**nvarchar (1024)**|ターゲット サーバーが特定の行を処理しているときにエラーが発生した場合のエラー メッセージ。|  
|**date_posted**|**DATETIME**|ジョブがターゲット サーバーに通知された日付と時刻。|  
|**date_downloaded**|**DATETIME**|ジョブが最後にダウンロードされた日付と時刻。|  
|**オンライン**|**tinyint**|ジョブの状態:<br /><br /> **0** = まだダウンロードされていません<br /><br /> **1** = 正常にダウンロードされました|  
|**deleted_object_name**|**sysname**|削除されたオブジェクトの名前。|  
  
 <sup>1</sup> **object_id**列の値には **-1**を指定できます。この値は、 **operation_code**列の値が DELETE の場合に ALL の値に対応します。  
  
  
