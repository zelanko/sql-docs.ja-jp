---
title: "SQL_VARIANT_PROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SQL_VARIANT_PROPERTY_TSQL
- SQL_VARIANT_PROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- SQL_VARIANT_PROPERTY function
- sql_variant data type
ms.assetid: 50e5c1d9-4e95-4ed0-9c92-435c872a399e
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 71ca2fac0a6b9f087f9d434c5a701f5656889b9e
ms.openlocfilehash: bd9b181c04a96ee90b0bbb54546a1d925761224f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/13/2017

---
# <a name="sqlvariantproperty-transact-sql"></a>SQL_VARIANT_PROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  に関する基本データ型とその他の情報を返します、 **sql_variant**値。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SQL_VARIANT_PROPERTY ( expression , property )  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 型の式は、 **sql_variant**です。  
  
 *プロパティ*  
 名前を含む、 **sql_variant**情報を指定するプロパティです。 *プロパティ*は**varchar (**128**)**、次の値のいずれかを指定できます。  
  
|値|Description|返される sql_variant の基本データ型|  
|-----------|-----------------|----------------------------------------|  
|**BaseType**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型など。<br /><br /> **bigint**<br /><br /> **[バイナリ]**<br /><br /> **char**<br /><br /> **date**<br /><br /> **datetime**<br /><br /> **datetime2**<br /><br /> **datetimeoffset**<br /><br /> **decimal**<br /><br /> **float**<br /><br /> **int**<br /><br /> **money**<br /><br /> **nchar**<br /><br /> **numeric**<br /><br /> **nvarchar**<br /><br /> **real**<br /><br /> **smalldatetime**<br /><br /> **smallint**<br /><br /> **smallmoney**<br /><br /> **time**<br /><br /> **tinyint**<br /><br /> **uniqueidentifier**<br /><br /> **varbinary**<br /><br /> **varchar**|**sysname**<br /><br /> NULL = 無効な入力|  
|**[精度]**|数値基本データ型の桁数です。<br /><br /> **datetime** 23 を =<br /><br /> **smalldatetime** 16 を =<br /><br /> **float** 53 を =<br /><br /> **real** 24 を =<br /><br /> **10 進**(p, s) と**数値**(p, s) = p<br /><br /> **money** 19 を =<br /><br /> **smallmoney** 10 を =<br /><br /> **bigint** 19 を =<br /><br /> **int** 10 を =<br /><br /> **smallint** = 5<br /><br /> **tinyint** 3 を =<br /><br /> **ビット**= 1<br /><br /> その他のすべてのデータ型 = 0|**int**<br /><br /> NULL = 無効な入力|  
|**[スケール]**|数値基本データ型の小数点の右側の桁数です。<br /><br /> **10 進**(p, s) と**数値**(p, s) = s<br /><br /> **money**と**smallmoney** 4 を =<br /><br /> **datetime** 3 を =<br /><br /> その他のすべての型 = 0|**int**<br /><br /> NULL = 無効な入力|  
|**TotalBytes**|メタデータと値のデータの両方を保持するのに必要なバイト数です。 この情報内のデータの最大サイズを調べるで役に立つ、 **sql_variant**列です。 値が 900 を超える場合は、インデックスの作成は失敗します。|**int**<br /><br /> NULL = 無効な入力|  
|**照合順序**|特定の照合順序を表す**sql_variant**値。|**sysname**<br /><br /> NULL = 無効な入力|  
|**MaxLength**|データの最大データ長 (バイト単位) です。 たとえば、 **MaxLength**の**nvarchar (**50**)** 100、 **MaxLength**の**int**は 4 です。|**int**<br /><br /> NULL = 無効な入力|  
  
## <a name="return-types"></a>戻り値の型  
 **sql_variant**  
  
## <a name="examples"></a>使用例  
### <a name="a-using-a-sqlvariant-in-a-table"></a>A. テーブルで、sql_variant 型の使用  
 次の例では取得`SQL_VARIANT_PROPERTY`については、`colA`値`46279.1`場所`colB`  =`1689`こと、`tableA`が`colA`型である`sql_variant`と`colB`.  
  
```sql    
CREATE   TABLE tableA(colA sql_variant, colB int)  
INSERT INTO tableA values ( cast (46279.1 as decimal(8,2)), 1689)  
SELECT   SQL_VARIANT_PROPERTY(colA,'BaseType') AS 'Base Type',  
         SQL_VARIANT_PROPERTY(colA,'Precision') AS 'Precision',  
         SQL_VARIANT_PROPERTY(colA,'Scale') AS 'Scale'  
FROM      tableA  
WHERE      colB = 1689  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]これら 3 つの値の各ことに注意してください、 **sql_variant**です。  
  
```  
Base Type    Precision    Scale  
---------    ---------    -----  
decimal      8           2  
  
(1 row(s) affected)  
```  
  
### <a name="b-using-a-sqlvariant-as-a-variable"></a>B. 変数として、sql_variant 型の使用   
 次の例では取得`SQL_VARIANT_PROPERTY`という名前の変数に関する情報@v1です。  
  
```sql    
DECLARE @v1 sql_variant;  
SET @v1 = 'ABC';  
SELECT @v1;  
SELECT SQL_VARIANT_PROPERTY(@v1, 'BaseType');  
SELECT SQL_VARIANT_PROPERTY(@v1, 'MaxLength');  
```  
  
## <a name="see-also"></a>参照  
 [sql_variant &#40;Transact-SQL&#41;](../../t-sql/data-types/sql-variant-transact-sql.md)  
  
  


