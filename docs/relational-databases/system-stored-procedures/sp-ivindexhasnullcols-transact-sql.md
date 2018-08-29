---
title: sp_ivindexhasnullcols (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a7ca9be2e67f49a2881171dcfb4e0a99a6672bd6
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023732"
---
# <a name="spivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インデックス付きビューを使ってトランザクション パブリケーションを作成する場合に、インデックス付きビューのクラスター化インデックスが一意であることと、NULL 値が許容される列を含まないことを検証します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [ **@viewname**=] **'***view_name***'**  
 検証するビューの名前を指定します。 *view_name*は**sysname**、既定値はありません。  
  
 [ **@fhasnullcols**=] *field_has_null_columns*出力  
 NULL が許容される列がビュー インデックスにあるかどうかを示すフラグです。 *view_name*は**sysname**、既定値はありません。 値を返します**1**場合は NULL が許容される列がビュー インデックスにします。 値を返します**0**ビューに NULL を許容する列が含まれていない場合。  
  
> [!NOTE]  
>  ストアド プロシージャ自体でのリターン コードを返すかどうか**1**、障害がストアド プロシージャの実行の意味、この値は**0**無視する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_ivindexhasnullcols**トランザクション レプリケーションで使用されます。  
  
 既定では、サブスクライバー側でパブリケーション内のインデックス付きビュー アーティクルはテーブルとして作成されます。 ただし、インデックス列で NULL 値が許容される場合、サブスクライバー側でインデックス付きビューはテーブルではなくインデックス付きビューとして作成されます。 このストアド プロシージャを実行することによって、現在のインデックス付きビューにこの問題があるかどうかをユーザーに知らせることができます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_ivindexhasnullcols**します。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
