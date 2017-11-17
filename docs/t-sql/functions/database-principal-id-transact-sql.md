---
title: "DATABASE_PRINCIPAL_ID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
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
- DATABASE_PRINCIPAL_ID_TSQL
- DATABASE_PRINCIPAL_ID
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], principals
- principal ID numbers [SQL Server]
- DATABASE_PRINCIPAL_ID function
- IDs [SQL Server], principals
ms.assetid: 908c7dd8-c10b-4658-92f6-0224f9835dd9
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0a26dcac49e19f9a0dda738e58042c83cb8e46b8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="databaseprincipalid-transact-sql"></a>DATABASE_PRINCIPAL_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

現在のデータベースでのプリンシパルの ID 番号を返します。 プリンシパルの詳細については、次を参照してください。[プリンシパル & #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DATABASE_PRINCIPAL_ID ( 'principal_name' )  
```  
  
## <a name="arguments"></a>引数  
*principal_name*  
型の式は、 **sysname**プリンシパルを表します。  
ときに*principal_name*は省略すると、現在のユーザーの ID が返されます。 かっこで囲む必要があります。
  
## <a name="return-types"></a>戻り値の型
**int**  
データベース プリンシパルが存在しない場合は NULL です。
  
## <a name="remarks"></a>解説  
DATABASE_PRINCIPAL_ID は、選択リスト内、WHERE 句内、または式が使える場所ならどこにでも使用できます。 詳細については、「[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)」を参照してください。
  
## <a name="examples"></a>使用例  
  
### <a name="a-retrieving-the-id-of-the-current-user"></a>A. 現在のユーザーの ID を取得する  
次の例では、現在のユーザーのデータベース プリンシパル ID を返します。
  
```sql
SELECT DATABASE_PRINCIPAL_ID();  
GO  
```  
  
### <a name="b-retrieving-the-id-of-a-specified-database-principal"></a>B. 指定されたデータベース プリンシパルの ID を取得する  
次の例は、データベース ロールのデータベース プリンシパル ID を返します`db_owner`です。
  
```sql
SELECT DATABASE_PRINCIPAL_ID('db_owner');  
GO  
```  
  
## <a name="see-also"></a>参照
[プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
[権限の階層 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)  
[sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)
  
  

