---
title: sp_grantdbaccess (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grantdbaccess
- sp_grantdbaccess_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantdbaccess
ms.assetid: 3eb09513-03f1-42f8-9917-3a1f3a579bec
ms.author: vanto
manager: craigg
ms.openlocfilehash: b35e2baef80dbacf039b9c767f7798ddba0d90a9
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591556"
---
# <a name="spgrantdbaccess-transact-sql"></a>sp_grantdbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースにデータベース ユーザーを追加します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[CREATE USER](../../t-sql/statements/create-user-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_grantdbaccess [ @loginame = ] 'login'  
    [ , [ @name_in_db = ] 'name_in_db' [ OUTPUT ] ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@loginame =** ] **'**_ログイン_ **'**  
 新しいデータベース ユーザーにマップされる Windows グループ、Windows ログイン、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの名前を指定します。 Windows グループと Windows ログインの名前は、フォームでの Windows ドメイン名で修飾する必要があります*ドメイン*\\*ログイン*。 たとえば、 **\joeb**します。 既にデータベース内のユーザーにマップされているログインは指定できません。 *ログイン*は、 **sysname**、既定値はありません。  
  
 [  **@name_in_db=**] **'**_name_in_db_**'** **[出力]**  
 新しいデータベース ユーザーの名前です。 *name_in_db* OUTPUT 変数のデータ型では、 **sysname**、および既定値は NULL です。 指定しない場合、*ログイン*使用されます。 値は null の場合、出力変数として指定されている場合**@name_in_db**に設定されている*ログイン*します。 *name_in_db*現在のデータベースに既に存在する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_grantdbaccess**呼び出しユーザーの作成、追加のオプションがサポートされます。 データベース ユーザーを作成する方法の詳細については、次を参照してください。 [CREATE USER &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)します。 データベースからデータベース ユーザーを削除するには使用[DROP USER](../../t-sql/statements/drop-user-transact-sql.md)します。  
  
 **sp_grantdbaccess**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、 **db_owner**固定データベース ロール、または**db_accessadmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、`CREATE USER` を使用して、Windows ログイン `Edmonds\LolanSo` 用のデータベース ユーザーを現在のデータベースに追加します。 新しいユーザーの名前は `Lolan` です。 データベース ユーザーの作成には、この方法を使用することをお勧めします。  
  
```  
CREATE USER Lolan FOR LOGIN [Edmonds\LolanSo];  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
