---
title: fulltext_catalogs (Transact-sql) |Microsoft Docs
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
ms.openlocfilehash: 114109e0ee7bf7ba8855ad65f4ab7438c9815187
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68133857"
---
# <a name="sysfulltext_catalogs-transact-sql"></a>sys.fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フルテキストカタログごとに1行の値を格納します。  
  
> [!NOTE]  
>  次の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列は、の将来のリリースで削除される予定です: **data_space_id**、 **file_id**、および**パス**。 新しい開発作業ではこれらの列を使用しないようにし、現在これらの列を使用しているアプリケーションはできるだけ早く修正してください。  
 
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|fulltext_catalog_id|**int**|フルテキストカタログの ID。 データベース内のフルテキストカタログ全体で一意です。|  
|name|**sysname**|カタログの名前。 データベース内で一意です。|  
|パス|**nvarchar(260)**|ファイルシステム内のカタログディレクトリの名前。|  
|is_default|**bit**|既定のフルテキストカタログ。<br /><br /> True = が既定値です。<br /><br /> False = 既定値ではない|  
|is_accent_sensitivity_on|**bit**|カタログのアクセントの区別に関する設定。<br /><br /> True = アクセントを区別する。<br /><br /> False = アクセントを区別しない|  
|data_space_id|**int**|このカタログが作成されたファイルグループ。|  
|file_id|**int**|カタログに関連付けられているフルテキストファイルのファイル ID。|  
|principal_id|**int**|フルテキストカタログを所有するデータベースプリンシパルの ID。|  
|is_importing|**bit**|フルテキストカタログがインポートされているかどうかを示します。<br /><br /> 1 = カタログがインポートされています。<br /><br /> 2 = カタログがインポートされていません。|  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [Transact-sql&#41;&#40;のフルテキストカタログの変更](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40;Transact-SQL&#41;](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)  
  
  
