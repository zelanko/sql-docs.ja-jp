---
title: sys.fulltext_catalogs (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
caps.latest.revision: 39
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 314fa09550ae3d9f5588dc2f382d6e5eba08e169
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysfulltextcatalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フルテキスト カタログごとに 1 行のデータを格納します。  
  
> [!NOTE]  
>  次の列は、の将来のリリースで削除される予定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **data_space_id**、 **file_id**、および**パス**です。 新規の開発作業ではこれらの列を使用しないようにし、現在これらの列を使用しているアプリケーションはできるだけ早く修正してください。  
 
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|フルテキスト カタログの ID です。 データベース内のフルテキスト カタログ全体で一意です。|  
|name|**sysname**|カタログの名前です。 データベース内で一意です。|  
|path|**nvarchar(260)**|ファイル システム内のカタログ ディレクトリの名前。|  
|is_default|**bit**|既定のフルテキスト カタログ。<br /><br /> True = 既定値<br /><br /> False = 既定値ではない|  
|is_accent_sensitivity_on|**bit**|カタログのアクセントの区別に関する設定。<br /><br /> True = アクセントを区別する<br /><br /> False = アクセントを区別しない|  
|data_space_id|**int**|カタログが作成されたファイル グループ。|  
|file_id|**int**|カタログに関連付けられているフルテキスト ファイルのファイル ID。|  
|principal_id|**int**|フルテキスト カタログを所有するデータベース プリンシパルの ID。|  
|is_importing|**bit**|フルテキスト カタログがインポートされているかどうかを示します。<br /><br /> 1 = カタログがインポートされています。<br /><br /> 2 = カタログがインポートされていません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [フルテキスト カタログ & #40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [ALTER FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)  
  
  
