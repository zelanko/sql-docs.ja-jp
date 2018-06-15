---
title: sp_dropuser (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_dropuser
- sp_dropuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropuser
ms.assetid: e28f18f9-7ecf-4568-89f4-fe5c520df386
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9af8a740ae349f748acc6c8385d95b97a0e2490d
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243199"
---
# <a name="spdropuser-transact-sql"></a>sp_dropuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースからデータベース ユーザーを削除します。 **sp_dropuser**の旧バージョンとの互換性を提供[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用して[DROP USER](../../t-sql/statements/drop-user-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropuser [ @name_in_db = ] 'user'  
```  
  
## <a name="arguments"></a>引数  
 [ **@name_in_db =**] **'***user***'**  
 削除するユーザーの名前を指定します。 *ユーザー*は、 **sysname**、既定値はありません。 *ユーザー*現在のデータベースに存在する必要があります。 Windows ログインを指定する場合は、データベースでログインとして認識されている名前を使用してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropuser**実行**sp_revokedbaccess**を現在のデータベースからユーザーを削除します。  
  
 使用して**sp_helpuser**現在のデータベースから削除できるユーザー名の一覧を表示します。  
  
 データベース ユーザーを削除すると、そのユーザーの別名も削除されます。 ユーザーが、ユーザー名と同じ空のスキーマを所有している場合、そのスキーマは削除されます。 ユーザーがデータベース内にその他のセキュリティ保護可能なリソースを所有している場合、ユーザーは削除されません。 まず、オブジェクトの所有権を別のプリンシパルに譲渡する必要があります。 詳細については、次を参照してください。 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md). データベース ユーザーを削除すると、そのユーザーに関連付けられている権限が自動的に削除されます。ユーザーは、メンバーとなっているデータベース ロールから削除されます。  
  
 **sp_dropuser**データベースの所有者を削除するのには使用できません (**dbo**) **INFORMATION_SCHEMA**ユーザー、または**ゲスト**からユーザーを**マスター**または**tempdb**データベース。 システム以外のデータベース、`EXEC sp_dropuser 'guest'`ユーザーの CONNECT 権限を取り消す**ゲスト**です。 ユーザー自身は残ります。  
  
 **sp_dropuser**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>権限  
 データベースに対する ALTER ANY USER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、ユーザーを削除する`Albert`現在のデータベースからです。  
  
```  
EXEC sp_dropuser 'Albert';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [DROP USER & #40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-user-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
