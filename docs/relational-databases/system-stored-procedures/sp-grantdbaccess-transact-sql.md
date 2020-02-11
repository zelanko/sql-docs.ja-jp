---
title: sp_grantdbaccess (Transact-sql) |Microsoft Docs
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
author: VanMSFT
ms.openlocfilehash: 3b88badb8b1852617d9edd8acd31f2c19258cca7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "72304865"
---
# <a name="sp_grantdbaccess-transact-sql"></a>sp_grantdbaccess (Transact-sql)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースにデータベース ユーザーを追加します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]代わりに[CREATE USER](../../t-sql/statements/create-user-transact-sql.md)を使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_grantdbaccess [ @loginame = ] 'login'  
    [ , [ @name_in_db = ] 'name_in_db' [ OUTPUT ] ]  
```  
  
## <a name="arguments"></a>引数  
`[ @loginame = ] 'login_ '`新しいデータベースユーザーにマップされる Windows グループ、Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン、またはログインの名前を指定します。 Windows グループと windows ログインの名前は、*ドメイン*\\*ログイン*形式の windows ドメイン名で修飾する必要があります。たとえば、 **LONDON\Joeb**のようになります。 ログインをデータベース内のユーザーにマップすることはできません。 *login*は**sysname**であり、既定値はありません。  
  
``[ @name_in_db = ] 'name_in_db' [ OUTPUT]``新しいデータベースユーザーの名前を指定します。 *name_in_db*のデータ型は**sysname**で、既定値は NULL です。 指定しない場合は、*ログイン*が使用されます。 値が NULL の出力変数として指定した場合、 ** \@name_in_db**は*login*に設定されます。 *name_in_db*は、現在のデータベースに存在していない必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_grantdbaccess**は、追加のオプションをサポートする CREATE USER を呼び出します。 データベースユーザーの作成の詳細については、「 [CREATE USER &#40;transact-sql&#41;](../../t-sql/statements/create-user-transact-sql.md)」を参照してください。 データベースからデータベースユーザーを削除するには、 [DROP user](../../t-sql/statements/drop-user-transact-sql.md)を使用します。  
  
 **sp_grantdbaccess**は、ユーザー定義のトランザクション内では実行できません。  
  
## <a name="permissions"></a>アクセス許可  
 **Db_owner**固定データベースロールまたは**db_accessadmin**固定データベースロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例で`CREATE USER`は、を使用して、Windows ログイン`Edmonds\LolanSo`のデータベースユーザーを現在のデータベースに追加します。 新しいユーザーの名前は `Lolan` です。 これは、データベースユーザーを作成するための推奨される方法です。  
  
```sql
CREATE USER Lolan FOR LOGIN [Edmonds\LolanSo];  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [ユーザー &#40;Transact-sql&#41;の作成](../../t-sql/statements/create-user-transact-sql.md)   
 [ユーザー &#40;Transact-sql&#41;を削除します。](../../t-sql/statements/drop-user-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
