---
title: sys.fulltext_catalogs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 0183694382851f023c9f6863848a3e525cc0b7aa
ms.sourcegitcommit: 04c031f7411aa33e2174be11dfced7feca8fbcda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2019
ms.locfileid: "64945619"
---
# <a name="sysfulltextcatalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各フルテキスト カタログの行を格納します。  
  
> [!NOTE]  
>  次の列は、の将来のリリースで削除が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **data_space_id**、 **file_id**、および**パス**します。 新しい開発作業でこれらの列を使用しないようにしこれらの列のいずれかをできるだけ早く使用されているアプリケーションを変更します。  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|フルテキスト カタログの ID。 データベースのフルテキスト カタログ全体で一意です。|  
|NAME|**sysname**|カタログの名前。 データベース内で一意です。|  
|path|**nvarchar(260)**|ファイル システム内のカタログ ディレクトリの名前です。|  
|is_default|**bit**|既定のフルテキスト カタログ。<br /><br /> True = 既定値です。<br /><br /> False = 既定値ではない|  
|is_accent_sensitivity_on|**bit**|カタログのアクセントの区別に関する設定。<br /><br /> True = アクセントを区別します。<br /><br /> False = アクセントを区別しない|  
|data_space_id|**int**|このカタログが作成されたファイル グループ。|  
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
  
  
