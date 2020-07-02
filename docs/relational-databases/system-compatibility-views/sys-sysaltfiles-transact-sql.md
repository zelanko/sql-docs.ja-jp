---
title: sys.sysaltfiles (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: 3c79b582eaf6ba6f4fef568af11110fcb6ea17c6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764394"
---
# <a name="syssysaltfiles-transact-sql"></a>sys.sysaltfiles (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  特別な状況では、には、データベース内のファイルに対応する行が含まれています。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|ファイルの識別番号。 これは、データベースごとに一意です。|  
|**groupid**|**smallint**|ファイルグループの id 番号。|  
|**size**|**int**|ファイル サイズ (8 KB ページ単位) です。|  
|**maxsize**|**int**|最大ファイル サイズ (8 KB ページ単位) です。<br /><br /> 0 = ファイル サイズが拡張しないことを表します。<br /><br /> -1 = ディスクがいっぱいになるまでファイル サイズが拡張します。<br /><br /> 268435456 = ログファイルは、最大サイズの 2 TB まで拡張されます。<br /><br /> 注: ログファイルのサイズを無制限にアップグレードしたデータベースは、ログファイルの最大サイズに対して-1 を報告します。|  
|**成長**|**int**|データベースの拡張サイズ。<br /><br /> 0 = ファイル サイズが拡張しないことを表します。 Status の値に応じて、ページ数またはファイルサイズのパーセンテージのいずれかになります。 **Status**が0x100000 の場合、**拡張**はファイルサイズの割合です。それ以外の場合は、ページ数になります。|  
|**status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**perf**|**int**|予約済み。|  
|**dbid**|**smallint**|このファイルが属するデータベースのデータベース識別番号です。|  
|**name**|**sysname**|ファイルの論理名です。|  
|**filename**|**nvarchar(260)**|物理デバイスの名前です。 これには、ファイルの完全パスが含まれます。|  
  
## <a name="see-also"></a>関連項目  
 [システムビューへのシステムテーブルのマッピング &#40;Transact-sql&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
