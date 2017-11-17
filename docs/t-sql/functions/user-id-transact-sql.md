---
title: "USER_ID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- USER_ID
- USER_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- USER_ID function
- identification numbers [SQL Server]
- IDs [SQL Server], databases
- users [SQL Server], database ID numbers
- database IDs [SQL Server]
- identification numbers [SQL Server], databases
ms.assetid: 67fd29bc-eda9-4d4d-b148-5d3659181a43
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a40853c10e17969c78ef88e4b75995e77b8a1bac
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="userid-transact-sql"></a>USER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  データベース ユーザーの ID 番号を返します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
USER_ID ( [ 'user' ] )  
```  
  
## <a name="arguments"></a>引数  
 *ユーザー*  
 使用するユーザー名を指定します。 *ユーザー*は**nchar**です。 場合、 **char**値を指定すると、暗黙的に変換されます**nchar**です。 かっこで囲む必要があります。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 ときに*ユーザー*は省略すると、現在のユーザーが想定されます。 パラメーターに NULL が含まれていると、NULL が返されます。EXECUTE AS の後で USER_ID が呼び出されると、USER_ID は権限を借用したコンテキストの ID を返します。  
  
 特定のデータベース ユーザーにマップされない Windows プリンシパルがグループのメンバーシップでデータベースにアクセスした場合、USER_ID では 0 (public の ID) が返されます。 このようなプリンシパルが、スキーマを指定せずにオブジェクトを作成する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]暗黙的なユーザーと Windows プリンシパルにマップするスキーマが作成されます。 このときに作成されたユーザーを使用して、データベースに接続することはできません。 暗黙のユーザーにマップされた Windows プリンシパルが USER_ID を呼び出すと、暗黙のユーザーの ID が返されます。  
  
 USER_ID は、選択リスト、WHERE 句、また、式を使える所ならどこにでも使用できます。 詳細については、「[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例は、の識別番号を返します、`AdventureWorks2012`ユーザー`Harold`です。  
  
```  
USE AdventureWorks2012;  
SELECT USER_ID('Harold');  
GO  
```  
  
## <a name="see-also"></a>参照  
 [USER_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-name-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [DATABASE_PRINCIPAL_ID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/database-principal-id-transact-sql.md)   
 [セキュリティ関数 &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

