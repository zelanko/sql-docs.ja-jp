---
title: sp_help_fulltext_catalog_components (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalog_components_TSQL
- sp_help_fulltext_catalog_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalog_components
ms.assetid: fbd6a3d4-6a4c-42a2-bff8-2a5eb0745e47
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 54c22d025ae809d035fe75a0b8fe89160bdfb84f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720370"
---
# <a name="sphelpfulltextcatalogcomponents-transact-sql"></a>sp_help_fulltext_catalog_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースにあるすべてのフルテキスト カタログに使用されている、すべてのコンポーネント (フィルター、ワード ブレーカー、プロトコル ハンドラー) の一覧を返します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_fulltext_catalog_components  
```  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**フルテキスト カタログ名**|**int**|フルテキスト カタログの名前。|  
|**フルテキスト カタログ id**|**sysname**|フルテキスト カタログの ID。|  
|**componenttype**|**sysname**|コンポーネントの型。 次のいずれかです。<br /><br /> Assert<br /><br /> プロトコル ハンドラー<br /><br /> ワード ブレーカー|  
|**componentname**|**sysname**|コンポーネント名。|  
|**clsid**|**uniqueidentifier**|コンポーネントのクラス ID。|  
|**fullpath**|**nvarchar (256)**|コンポーネントの場所へのパス。<br /><br /> NULL のメンバーでない呼び出し元を = **serveradmin**固定サーバー ロール。|  
|**version**|**nvarchar(30)**|コンポーネントのバージョンです。|  
|**manufacturer**|**sysname**|コンポーネントの製造元の名前。|  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [フルテキスト検索およびセマンティック検索ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [sys.fulltext_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_system_components &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  
