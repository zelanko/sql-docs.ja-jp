---
title: "sys.sysdevices (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df1376d568b0b95952f57251d1f2b32fe9680a52
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディスク バックアップ ファイル、テープ バックアップ ファイル、およびデータベース ファイルごとに 1 行のデータを格納します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|バックアップ ファイルまたはデータベース ファイルの論理名。|  
|**size**|**int**|ファイルのサイズ (2 KB ページ単位)。|  
|**low**|**int**|旧バージョンとの互換性のためにだけ用意されています。|  
|**high**|**int**|旧バージョンとの互換性のためにだけ用意されています。|  
|**ステータス**|**smallint**|デバイスの種類を示すビットマップ。<br /><br /> 1 = 既定のディスク<br /><br /> 2 = 物理ディスク<br /><br /> 4 = 論理ディスク<br /><br /> 8 = ヘッダーをスキップ<br /><br /> 16 = バックアップ ファイル<br /><br /> 32 = シリアル書き込み<br /><br /> 4096 = 読み取り専用|  
|**cntrltype**|**smallint**|コント ローラーの種類:<br /><br /> 0 = CD-ROM 以外のデータベース ファイル<br /><br /> 2 = ディスク バックアップ ファイル<br /><br /> 3 - 4 = フロッピー ディスク バックアップ ファイル<br /><br /> 5 = テープ バックアップ ファイル<br /><br /> 6 = 名前付きパイプ ファイル|  
|**phyname**|**nvarchar(260)**|物理ファイルの名前。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
