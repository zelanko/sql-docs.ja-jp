---
title: sys.fulltext_catalogs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_catalogs_TSQL
- sys.fulltext_catalogs
- fulltext_catalogs
- fulltext_catalogs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_catalogs catalog view
ms.assetid: cf1489ff-4819-41fa-a62a-4ed797a16207
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d4f6099b6f741dd5f0f29687cacc37e6cdfe6fb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47712170"
---
# <a name="sysfulltextcatalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フルテキスト カタログごとに 1 行のデータを格納します。  
  
> [!NOTE]  
>  次の列は、の将来のリリースで削除が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **data_space_id**、 **file_id**、および**パス**します。 新規の開発作業ではこれらの列を使用しないようにし、現在これらの列を使用しているアプリケーションはできるだけ早く修正してください。  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|フルテキスト カタログの ID。 データベース内のフルテキスト カタログ全体で一意です。|  
|NAME|**sysname**|カタログの名前。 データベース内で一意です。|  
|path|**nvarchar(260)**|ファイル システム内のカタログ ディレクトリの名前。|  
|is_default|**bit**|既定のフルテキスト カタログ。<br /><br /> True = 既定値<br /><br /> False = 既定値ではない|  
|is_accent_sensitivity_on|**bit**|カタログのアクセントの区別に関する設定。<br /><br /> True = アクセントを区別する<br /><br /> False = アクセントを区別しない|  
|data_space_id|**int**|カタログが作成されたファイル グループ。|  
|file_id|**int**|カタログに関連付けられているフルテキスト ファイルのファイル ID。|  
|principal_id|**int**|フルテキスト カタログを所有するデータベース プリンシパルの ID。|  
|is_importing|**bit**|フルテキスト カタログがインポートされているかどうかを示します。<br /><br /> 1 = カタログがインポートされています。<br /><br /> 2 = カタログがインポートされていません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)  
  
  
