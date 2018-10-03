---
title: sys.sysreferences (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysreferences
- sys.sysreferences_TSQL
- sysreferences
- sysreferences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysreferences compatibility view
- sysreferences system table
ms.assetid: 81276f13-202e-4e74-962d-46eb98c98d2e
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 10409e8655925e9ead7c5954332567aded0dc184
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47643466"
---
# <a name="syssysreferences-transact-sql"></a>sys.sysreferences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  参照される列への FOREIGN KEY 制約定義のマッピングをデータベース内に保持します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|FOREIGN KEY 制約の ID です。|  
|**fkeyid**|**int**|参照しているテーブルの ID です。|  
|**rkeyid**|**int**|参照されるテーブルの ID です。|  
|**rkeyindid**|**smallint**|参照されるキー列を含む参照されるテーブルにおける、一意なインデックスのインデックス ID です。|  
|**keycnt**|**smallint**|キー内の列数です。|  
|**forkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**fkeydbid**|**smallint**|予約されています。|  
|**rkeydbid**|**smallint**|予約されています。|  
|**fkey1**|**smallint**|参照している列の ID です。|  
|**fkey2**|**smallint**|参照している列の ID です。|  
|**fkey3**|**smallint**|参照している列の ID です。|  
|**fkey4**|**smallint**|参照している列の ID です。|  
|**fkey5**|**smallint**|参照している列の ID です。|  
|**fkey6**|**smallint**|参照している列の ID です。|  
|**fkey7**|**smallint**|参照している列の ID です。|  
|**fkey8**|**smallint**|参照している列の ID です。|  
|**fkey9**|**smallint**|参照している列の ID です。|  
|**fkey10**|**smallint**|参照している列の ID です。|  
|**fkey11**|**smallint**|参照している列の ID です。|  
|**fkey12**|**smallint**|参照している列の ID です。|  
|**fkey13**|**smallint**|参照している列の ID です。|  
|**fkey14**|**smallint**|参照している列の ID です。|  
|**fkey15**|**smallint**|参照している列の ID です。|  
|**fkey16**|**smallint**|参照している列の ID です。|  
|**rkey1**|**smallint**|参照される列の ID です。|  
|**rkey2**|**smallint**|参照される列の ID です。|  
|**rkey3**|**smallint**|参照される列の ID です。|  
|**rkey4**|**smallint**|参照される列の ID です。|  
|**rkey5**|**smallint**|参照される列の ID です。|  
|**rkey6**|**smallint**|参照される列の ID です。|  
|**rkey7**|**smallint**|参照される列の ID です。|  
|**rkey8**|**smallint**|参照される列の ID です。|  
|**rkey9**|**smallint**|参照される列の ID です。|  
|**rkey10**|**smallint**|参照される列の ID です。|  
|**rkey11**|**smallint**|参照される列の ID です。|  
|**rkey12**|**smallint**|参照される列の ID です。|  
|**rkey13**|**smallint**|参照される列の ID です。|  
|**rkey14**|**smallint**|参照される列の ID です。|  
|**rkey15**|**smallint**|参照される列の ID です。|  
|**rkey16**|**smallint**|参照される列の ID です。|  
  
## <a name="see-also"></a>参照  
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
