---
title: sys.sysaltfiles (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysaltfiles_TSQL
- sys.sysaltfiles
- sysaltfiles_TSQL
- sysaltfiles
dev_langs:
- TSQL
helpviewer_keywords:
- sysaltfiles system table
- sys.sysaltfiles compatibility view
ms.assetid: 698dec23-5336-4108-87a5-f8e407f8da09
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 941b51b6e05fd88a8b59b8e4f3b28ee145affe3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636560"
---
# <a name="syssysaltfiles-transact-sql"></a>sys.sysaltfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特殊な状況では、データベース内のファイルに対応する行が含まれます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|ファイルの識別番号です。 この番号は、データベースごとに一意です。|  
|**groupid**|**smallint**|ファイル グループの識別番号です。|  
|**size**|**int**|ファイル サイズ (8 KB ページ単位) です。|  
|**maxsize**|**int**|最大ファイル サイズ (8 KB ページ単位) です。<br /><br /> 0 = ファイル サイズが拡張しないことを表します。<br /><br /> -1 = ディスクがいっぱいになるまでファイル サイズが拡張します。<br /><br /> 268435456 = ログ ファイルが最大 2 TB まで拡張することを表します。<br /><br /> 注: 無制限のログ ファイルのサイズにアップグレードしたデータベースは、ログ ファイルの最大サイズに達すると-1 に報告されます。|  
|**growth**|**int**|データベース サイズの増分値です。<br /><br /> 0 = ファイル サイズが拡張しないことを表します。 ステータスの値に応じて、ページ数またはファイル サイズのパーセンテージのいずれかの値をとります。 場合**状態**0x100000 は、**成長**それ以外のサイズの割合がファイル、ページの数です。|  
|**status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**perf**|**int**|予約されています。|  
|**dbid**|**smallint**|このファイルが属するデータベースのデータベース識別番号です。|  
|**name**|**sysname**|ファイルの論理名です。|  
|**filename**|**nvarchar(260)**|物理デバイスの名前です。 ファイルの完全なパスが含まれます。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
