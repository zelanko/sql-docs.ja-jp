---
title: sp_droprole (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_droprole
- sp_droprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprole
ms.assetid: 889ee074-00f8-40a9-bddb-d7d3ef0cbc19
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 6de087885b04b68cddfa7990705a217fbece5caa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spdroprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースからデータベース ロールを削除します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 **Sp_droprole** DROP ROLE ステートメントに置き換えられました。 **sp_droprole**が以前のバージョンと互換性のためだけに含まれる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]将来のリリースではサポートされない可能性があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>引数  
 [  **@rolename =** ] **'***ロール***'**  
 現在のデータベースから削除するデータベース ロールの名前を指定します。 *ロール*は、 **sysname**、既定値はありません。 *ロール*現在のデータベースに既に存在する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 使用してデータベース ロールのみを削除することができます**sp_droprole**です。  
  
 メンバーが既に存在するデータベース ロールは削除できません。 データベース ロールを削除するには、あらかじめそのデータベース ロールのすべてのメンバーを削除しておく必要があります。 ロールからユーザーを削除するには使用**sp_droprolemember の各**です。 すべてのユーザーは、ロールのメンバーではまだ場合**sp_droprole**それらのメンバーが表示されます。  
  
 固定ロールと**パブリック**ロールは削除できません。  
  
 ロールがセキュリティ保護可能なリソースを所有している場合、そのロールは削除できません。 セキュリティ保護可能なリソースを所有しているアプリケーション ロールを削除するには、先にセキュリティ保護可能なリソースの所有権を譲渡するか削除する必要があります。 削除禁止のオブジェクトの所有者を変更するには、ALTER AUTHORIZATION を使用します。  
  
 **sp_droprole**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>権限  
 ロールに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、アプリケーション ロール `Sales` を削除します。  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
