---
title: "IS_MEMBER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_MEMBER
- IS_MEMBER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], members
- current member status
- roles [SQL Server], members
- testing member status
- members [SQL Server]
- checking member status
- IS_MEMBER function
- verifying member status
- groups [SQL Server], members
- members [SQL Server], verifying
ms.assetid: 77cb68a0-19b7-4fe1-ab17-e5587699631b
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: e14fc4cf70066c21a8a837760d4325a19ae4ff1c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ismember-transact-sql"></a>IS_MEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のユーザーがの指定したメンバーであるかどうかを示す[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows グループまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース ロール。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
IS_MEMBER ( { 'group' | 'role' } )  
```  
  
## <a name="arguments"></a>引数  
 **'** *グループ* **'**  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 チェックされる Windows グループの名前を指定します形式である必要があります*ドメイン*\\*グループ*です。 *グループ*は**sysname**です。  
  
 **'** *ロール* **'**  
 名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]チェックされるロールです。 *ロール*は**sysname**データベース ロールまたはユーザー定義のロールではないサーバーの役割の固定を含めることができます。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 IS_MEMBER は、次の値を返します。  
  
|戻り値|Description|  
|------------------|-----------------|  
|0|現在のユーザーがのメンバーではない*グループ*または*ロール*です。|  
|1|現在のユーザーのメンバーである*グループ*または*ロール*です。|  
|NULL|いずれか*グループ*または*ロール*が無効です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインや、アプリケーション ロールを使用しているログインでクエリを実行した場合、Windows グループに対しては NULL が返されます。|  
  
 IS_MEMBER は、Windows によって作成されたアクセス トークンを調べることによって Windows グループ メンバーシップを決定します。 アクセス トークンは、ユーザーがのインスタンスに接続した後に行われたグループ メンバーシップの変更を反映していない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 Windows グループのメンバーシップをクエリできません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]アプリケーション ロールです。  
  
 追加し、データベース ロールからメンバーを削除を使用して[ALTER ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-role-transact-sql.md). 追加し、サーバー ロールからメンバーを削除を使用して[ALTER SERVER ROLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 この関数で評価されるのはロールのメンバーシップであって、基になる権限ではありません。 たとえば、 **db_owner**固定データベース ロールには、 **CONTROL DATABASE**権限です。 ユーザーがある場合、 **CONTROL DATABASE**権限はない、ロールのメンバーと、この関数は、ユーザーがのメンバーではないことを報告して正しく、 **db_owner**ロールで、ユーザーがある同じ場合でもアクセス許可です。  
  
 メンバー、 **sysadmin**を入力としてすべてのデータベースの固定サーバー ロール、 **dbo**ユーザー。 メンバーの権限は確認、 **sysadmin**固定サーバー ロールのアクセス許可をチェックする**dbo**、元のログインではありません。 **Dbo**データベース ロールに追加することはできませんし、Windows グループが存在しない**dbo**常に 0 (または、ロールが存在しない場合は NULL) を返します。  
  
## <a name="related-functions"></a>関連する関数  
 別のかを判断する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインがデータベース ロールのメンバーを使用して[IS_ROLEMEMBER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-rolemember-transact-sql.md). 確認するかどうか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン サーバー ロールのメンバーを使用して[IS_SRVROLEMEMBER (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="examples"></a>使用例  
 次の例は、現在のユーザーがデータベース ロールまたは Windows ドメイン グループのメンバーであるかどうかを確認します。  
  
```  
-- Test membership in db_owner and print appropriate message.  
IF IS_MEMBER ('db_owner') = 1  
   PRINT 'Current user is a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') = 0  
   PRINT 'Current user is NOT a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') IS NULL  
   PRINT 'ERROR: Invalid group / role specified';  
GO  
  
-- Execute SELECT if user is a member of ADVWORKS\Shipping.  
IF IS_MEMBER ('ADVWORKS\Shipping') = 1  
   SELECT 'User ' + USER + ' is a member of ADVWORKS\Shipping.';   
GO  
```  
  
## <a name="see-also"></a>参照  
 [IS_SRVROLEMEMBER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  
