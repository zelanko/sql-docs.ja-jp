---
title: "TYPE_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- TYPE_NAME_TSQL
- TYPE_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- names [SQL Server], data types
- unqualified type names
- type names [SQL Server]
- data types [SQL Server], names
- TYPE_NAME function
ms.assetid: e4075a2e-5f70-440f-986b-9ec8434e07c1
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d3d60bec3a21bb5b1127b0f18977d3485979f20b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="typename-transact-sql"></a>TYPE_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定した型の ID について、修飾なしの名前を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
TYPE_NAME ( type_id )   
```  
  
## <a name="arguments"></a>引数  
 *type_id*  
 使用する型の ID を指定します。 *type_id*は、 **int**、呼び出し元へのアクセス許可を持つ任意のスキーマ内の型を参照できます。  
  
## <a name="return-types"></a>戻り値の型  
 **sysname**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーは、ユーザーが所有するまたはをユーザーが許可されているアクセス許可のセキュリティ保護可能なメタデータのみを表示できます。 つまり、ユーザーがオブジェクトに対する権限を与えられていない場合、メタデータを生成する TYPE_NAME などの組み込み関数では NULL が返される可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 TYPE_NAME が返されます場合、NULL *type_id*が正しくないかと、呼び出し元がない型を参照するための十分なアクセス許可。  
  
 TYPE_NAME は、システム データ型と、ユーザー定義データ型にも使用できます。 型が含まれるスキーマはあらゆるスキーマが対象になりますが、常に修飾なしの名前が返されます。 つまり、名前が必要ない、*スキーマ***です。** プレフィックス。  
  
 システム関数は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。 詳細については、次を参照してください。[式 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)と[場所 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md).  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの `Vendor` テーブルにある各列の、オブジェクト名、列名、型名を返します。  
  
```  
SELECT o.name AS obj_name, c.name AS col_name,  
       TYPE_NAME(c.user_type_id) AS type_name  
FROM sys.objects AS o   
JOIN sys.columns AS c  ON o.object_id = c.object_id  
WHERE o.name = 'Vendor'  
ORDER BY col_name;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
obj_name        col_name                  type_name
--------------- ------------------------ --------------
Vendor          AccountNumber            AccountNumber
Vendor          ActiveFlag               Flag
Vendor          BusinessEntityID         int
Vendor          CreditRating             tinyint
Vendor          ModifiedDate             datetime
Vendor          Name                     Name
Vendor          PreferredVendorStatus    Flag
Vendor          PurchasingWebServiceURL  nvarchar

(8 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例を返します、 `TYPE ID` id を持つデータ型の`1`します。  
  
```  
SELECT TYPE_NAME(36) AS Type36, TYPE_NAME(239) AS Type239;  
GO  
```  
  
 型の一覧は、sys.types を照会します。  
  
```  
SELECT * FROM sys.types;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [TYPE_ID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/type-id-transact-sql.md)   
 [TYPEPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/typeproperty-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)   
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)  
  
  


