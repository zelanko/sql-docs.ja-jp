---
title: sp_fulltext_database (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
caps.latest.revision: 45
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 8f4904de1142052a8286aabb4a69bf439871b84e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spfulltextdatabase-transact-sql"></a>sp_fulltext_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト カタログにも何も起こりません[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降のバージョンと旧バージョンとの互換性を保つのためにサポートされてです。 **sp_fulltext_database**は指定されたデータベースの Full-text Engine を無効になりません。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でユーザーが作成したすべてのデータベースでは、常にフルテキスト インデックスが有効になっています。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]使用して[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>引数  
 [  **@action=**] **'***アクション***'**  
 実行する操作を指定します。 **アクション**は**varchar (20)**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**enable**|旧バージョンとの互換性のためにのみサポートされています。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンのフルテキスト カタログには影響しません。|  
|**disable**|旧バージョンとの互換性のためにのみサポートされています。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンのフルテキスト カタログには影響しません。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、フルテキスト インデックスを無効にすることはできません。 フルテキスト インデックス作成を無効にするから行が削除されません**sysfulltextcatalogs**されフルテキスト有効なテーブルがフルテキスト インデックス作成を不要になったマークされていることを示していません。 すべてのフルテキスト メタデータ定義はシステム テーブルに残ります。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールと**db_owner**固定データベース ロールが実行できる**sp_fulltext_database**です。  
  
## <a name="see-also"></a>参照  
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
