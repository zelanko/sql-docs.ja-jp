---
title: "COL_NAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COL_NAME
- COL_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- COL_NAME function
- column names [SQL Server]
- names [SQL Server], columns
ms.assetid: 214144ab-f2bc-4052-83cf-caf0a85c4cc6
caps.latest.revision: 28
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 77c7eb1fcde9b073b3c08f412ac0e46519763c74
ms.openlocfilehash: c697b619907bb3d80fbbff800b2ac29ef574af8d
ms.contentlocale: ja-jp
ms.lasthandoff: 10/17/2017

---
# <a name="colname-transact-sql"></a>COL_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

指定したテーブルの ID 番号および列の ID 番号から、その列の名前を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
COL_NAME ( table_id , column_id )  
```  
  
## <a name="arguments"></a>引数  
*table_id*  
列を含むテーブルの ID 番号を指定します。 *table_id*の種類は**int**です。
  
*column_id*  
列の ID 番号を指定します。 *column_id*パラメーターの型は**int**です。
  
## <a name="return-types"></a>戻り値の型
**sysname**
  
## <a name="exceptions"></a>例外  
エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。
  
ユーザーが所有しているか、または権限を与えられている、セキュリティ保護可能なリソースのメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (COL_NAME など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。
  
## <a name="remarks"></a>解説  
*Table_id*と*column_id*パラメーターは同時に、列名文字列を生成します。
  
テーブルと列の id 番号の取得の詳細については、次を参照してください。 [OBJECT_ID (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-id-transact-sql.md).
  
## <a name="examples"></a>使用例  
次の例は、サンプルでは、最初の列の名前を返します`Employee`テーブル。
  
```sql
-- Uses AdventureWorks  
  
SELECT COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 1) AS FirstColumnName,  
COL_NAME(OBJECT_ID('dbo.FactResellerSales'), 2) AS SecondColumnName;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
ColumnName          
------------   
BusinessEntityID  
```  
  
## <a name="see-also"></a>参照
[式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
[メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)  
[COLUMNPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/columnproperty-transact-sql.md)  
[COL_LENGTH & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/col-length-transact-sql.md)
  
  


