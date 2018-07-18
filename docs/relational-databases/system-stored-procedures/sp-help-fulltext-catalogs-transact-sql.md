---
title: sp_help_fulltext_catalogs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalogs_TSQL
- sp_help_fulltext_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalogs
ms.assetid: 1b94f280-e095-423f-88bc-988c9349d44c
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 5490c7e8d8658ddc8048e63d082d48ea92249c08
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37989354"
---
# <a name="sphelpfulltextcatalogs-transact-sql"></a>sp_help_fulltext_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したフルテキスト カタログの ID、名前、ルート ディレクトリ、ステータス、およびフルテキスト インデックスが作成されたテーブルの数を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用して、 [sys.fulltext_catalogs](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)カタログ ビューを代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_fulltext_catalogs [ @fulltext_catalog_name = ] 'fulltext_catalog_name'  
```  
  
## <a name="arguments"></a>引数  
 [ **@fulltext_catalog_name=**] **'***fulltext_catalog_name***'**  
 フルテキスト カタログの名前を指定します。 *fulltext_catalog_name*は**sysname**します。 このパラメーターを省略するか、NULL 値を指定した場合は、現在のデータベースに関連付けられたすべてのフルテキスト カタログに関する情報が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または (1) の失敗  
  
## <a name="result-sets"></a>結果セット  
 この表の順番で結果セット**ftcatid**します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**fulltext_catalog_id**|**smallint**|フルテキスト カタログ識別子。|  
|**NAME**|**sysname**|フルテキスト カタログの名前。|  
|**PATH**|**nvarchar(260)**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降、この句は無効です。|  
|**状態**|**int**|カタログのフルテキスト インデックスの作成ステータス。<br /><br /> 0 = アイドル状態<br /><br /> 1 = カタログ全体を作成中<br /><br /> 2 = 一時停止<br /><br /> 3 = 絞込み<br /><br /> 4 = 復旧<br /><br /> 5 = シャットダウン<br /><br /> 6 = 増分作成中<br /><br /> 7 = インデックス作成<br /><br /> 8 = ディスク容量不足、 一時停止<br /><br /> 9 = 変更の追跡<br /><br /> NULL = ユーザーがフルテキスト カタログに対する VIEW 権限を持っていない、データベースでフルテキストが有効になっていない。またはフルテキスト コンポーネントがインストールされていない|  
|**NUMBER_FULLTEXT_TABLES**|**int**|カタログに関連付けられた、フルテキスト インデックスが作成されたテーブルの数。|  
  
## <a name="permissions"></a>アクセス許可  
 実行権限は、既定のメンバーに、**パブリック**ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、フルテキスト カタログ `Cat_Desc` に関する情報を返します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help_fulltext_catalogs 'Cat_Desc' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_catalog &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
