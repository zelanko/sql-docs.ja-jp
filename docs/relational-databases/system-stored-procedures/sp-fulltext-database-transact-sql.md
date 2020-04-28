---
title: sp_fulltext_database (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_database_TSQL
- sp_fulltext_database
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_database
ms.assetid: eeb1e151-eb00-484c-8fd1-5641e621ffc6
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0c27f2efcfc15cc1ff9d53f735c08fad922f9466
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124278"
---
# <a name="sp_fulltext_database-transact-sql"></a>sp_fulltext_database (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  以降のバージョンの[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]フルテキストカタログには影響しません。旧バージョンとの互換性のためにのみサポートされています。 **sp_fulltext_database**は、指定されたデータベースのフルテキストエンジンを無効にしません。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でユーザーが作成したすべてのデータベースでは、常にフルテキスト インデックスが有効になっています。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 代わりに [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_fulltext_database [@action=] 'action'  
```  
  
## <a name="arguments"></a>引数  
`[ @action = ] 'action'`実行するアクションを指定します。 **アクション**は**varchar (20)**,、これらの値のいずれかを指定することができます。  
  
|値|説明|  
|-----------|-----------------|  
|**を**|旧バージョンとの互換性のためにのみサポートされています。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンのフルテキスト カタログには影響しません。|  
|**切り替える**|旧バージョンとの互換性のためにのみサポートされています。 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンのフルテキスト カタログには影響しません。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 None  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンでは、フルテキスト インデックスを無効にすることはできません。 フルテキストインデックス作成を無効にしても、 **sysfulltextcatalogs**から行は削除されず、フルテキストインデックスが有効になっているテーブルにはフルテキストインデックスが設定されていないことが示されません。 すべてのフルテキストメタデータ定義は、システムテーブルに残ります。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_fulltext_database**を実行できるのは、 **sysadmin**固定サーバーロールおよび**db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [DATABASEPROPERTYEX &#40;Transact-sql&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [FULLTEXTSERVICEPROPERTY &#40;Transact-sql&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
