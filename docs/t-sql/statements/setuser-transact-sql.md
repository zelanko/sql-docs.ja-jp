---
title: "SETUSER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SETUSER_TSQL
- SETUSER
dev_langs:
- TSQL
helpviewer_keywords:
- delegation [SQL Server]
- impersonation [SQL Server]
- SETUSER statement
- user impersonation [SQL Server]
ms.assetid: 7acfac5c-9ad6-4226-b874-7add36c4ea43
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ab9805dda5f5b2b4199cb40ef3c28af1d5b4379f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="setuser-transact-sql"></a>SETUSER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  メンバーは、 **sysadmin**固定サーバー ロールまたは別のユーザーの権限を借用するデータベースの所有者。  
  
> [!IMPORTANT]  
>  SETUSER は旧バージョンとの互換性のためだけに用意されています。 SETUSER は、の将来のリリースではサポートされない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 使用することをお勧め[EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SETUSER [ 'username' [ WITH NORESET ] ]   
```  
  
## <a name="arguments"></a>引数  
 **'** *username* **'**  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または権限が借用される現在のデータベース内の Windows ユーザーです。 ときに*username*が指定されていない、システム管理者またはデータベース所有者が、ユーザーの偽装の元の id をリセットします。  
  
 WITH NORESET  
 後続のことを示す SETUSER ステートメント (が指定されていない*username*) システム管理者またはデータベース所有者に、ユーザー id をリセットする必要があります。  
  
## <a name="remarks"></a>解説  
 SETUSER のメンバーで使用できる、 **sysadmin**固定サーバー ロールまたはその他のユーザーの権限をテストする別のユーザー id を借用するデータベースの所有者。 Db_owner 固定データベース ロールのメンバーシップが十分ではありません。  
  
 のみ SETUSER を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー。 SETUSER は Windows ユーザーに対してはサポートされていません。 SETUSER を使用して別のユーザーの ID の権限を借用している場合、権限を借用しているユーザーが作成するすべてのオブジェクトは、権限を借用されているユーザーによって所有されます。 たとえば、データベースの所有者には、ユーザーの id が前提としています**Margaret**というテーブルを作成および**orders**、 **orders**テーブルを所有**Margaret**、システム管理者ではありません。  
  
 SETUSER ステートメントは、別の SETUSER ステートメントを実行するか、現在のデータベースを USE ステートメントで変更するまで有効になります。  
  
> [!NOTE]  
>  SETUSER WITH NORESET を使用すると、データベース所有者またはシステム管理者が自分の権限を回復するには、いったんログ オフしてからもう一度ログ オンするしかありません。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **sysadmin**固定サーバー ロールまたはデータベースの所有者である必要があります。 メンバーシップ、 **db_owner**固定データベース ロールが不十分  
  
## <a name="examples"></a>使用例  
 この例では、データベース所有者が別のユーザーの ID を借用する方法を示します。 ユーザー`mary`という名前のテーブルが作成`computer_types`です。 SETUSER を使用して、データベース所有者権限を借用`mary`ユーザーに与える`joe`へのアクセス、`computer_types`テーブル、および自分独自の id をリセットします。  
  
```  
SETUSER 'mary';  
GO  
GRANT SELECT ON computer_types TO joe;  
GO  
--To revert to the original user  
SETUSER;  
```  
  
## <a name="see-also"></a>参照  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)  
  
  

