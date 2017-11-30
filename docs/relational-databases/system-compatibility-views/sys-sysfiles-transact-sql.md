---
title: "sys.sysfiles (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysfiles
- sys.sysfiles_TSQL
- sys.sysfiles
- sysfiles_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sysfiles system table
- sys.sysfiles compatibility view
ms.assetid: 3b47f38d-1cff-404d-89d3-9342c451c802
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7190a2389fc1504cb8068eb5ea9b6ffd7ed127fb
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="syssysfiles-transact-sql"></a>sys.sysfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース内のファイルごとに 1 行のデータを保持します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|各データベースで一意なファイル ID 番号です。|  
|**groupid**|**smallint**|ファイル グループの識別番号です。|  
|**サイズ**|**int**|ファイルのサイズ (8 KB ページ単位) です。|  
|**maxsize**|**int**|最大ファイル サイズ (8 KB ページ単位) です。<br /><br /> 0 = ファイル サイズが拡張しないことを表します。<br /><br /> -1 = ディスクがいっぱいになるまでファイル サイズが拡張します。<br /><br /> 268435456 = ログ ファイルが最大 2 TB まで拡張することを表します。<br /><br /> 注: が無制限のログ ファイル サイズとアップグレードされたデータベースは、ログ ファイルの最大サイズに達すると-1 に報告されます。|  
|**成長**|**int**|データベース サイズの増分値です。 ページ数またはの値に応じて、ファイル サイズのパーセンテージのいずれかを指定できます**ステータス**です。<br /><br /> 0 = ファイル サイズが拡張しないことを表します。|  
|**ステータス**|**int**|ステータス ビットです、**成長**メガバイト (MB) またはキロバイト (KB) のいずれかの値。<br /><br /> 0x2 = ディスク ファイル。<br /><br /> 0x40 = ログ ファイル。<br /><br /> 0x100000 = 拡張。 この値は、パーセンテージであり、ページ数ではありません。|  
|**パフォーマンス**|**int**|予約されています。|  
|**name**|**sysname**|ファイルの論理名です。|  
|**ファイル名**|**nvarchar (260)**|物理デバイスの名前です。 ファイルの完全なパスが含まれます。|  
  
## <a name="see-also"></a>参照  
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
