---
title: sp_revokedbaccess (TRANSACT-SQL) |Microsoft Docs
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
- sp_revokedbaccess_TSQL
- sp_revokedbaccess
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokedbaccess
ms.assetid: c997cfa1-539d-485c-a664-9c6f76bfe0c2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: f349df1368e3beac9c84ea56cde85828125ec280
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032932"
---
# <a name="sprevokedbaccess-transact-sql"></a>sp_revokedbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースからデータベース ユーザーを削除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[DROP USER](../../t-sql/statements/drop-user-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_revokedbaccess [ @name_in_db = ] 'name'  
```  
  
## <a name="arguments"></a>引数  
 [ **@name_in_db =** ] **'***name***'**  
 削除するデータベース ユーザーの名前を指定します。 *名前*は、 **sysname**既定値はありません。 *名前*サーバー ログイン、Windows ログイン、または Windows グループの名前を指定でき、現在のデータベースに存在する必要があります。 Windows ログインまたは Windows グループを指定する場合は、データベースで認識される名前を指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 データベース ユーザーを削除すると、そのユーザーに従属する権限や別名も自動的に削除されます。  
  
 **sp_revokedbaccess**現在のデータベースからデータベース ユーザーのみを削除することができます。 現在のデータベースにオブジェクトを所有しているデータベース ユーザーを削除する前には、オブジェクトの所有権を譲渡するか、オブジェクトをデータベースから削除する必要があります。 詳細については、次を参照してください。 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 **sp_revokedbaccess**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 データベースに対する ALTER ANY USER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例にマップされるデータベース ユーザーを削除する`Edmonds\LolanSo`現在のデータベースから。  
  
```  
EXEC sp_revokedbaccess 'Edmonds\LolanSo';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
