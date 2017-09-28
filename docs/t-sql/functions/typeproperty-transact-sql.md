---
title: "TYPEPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TYPEPROPERTY
- TYPEPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], data types
- data types [SQL Server], status information
- TYPEPROPERTY function
ms.assetid: bc311c80-bac5-46ab-a5c8-68b1c6bbf24a
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9b0cfaf45b7b4f68979691272c90962da42709b2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="typeproperty-transact-sql"></a>TYPEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データ型に関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
TYPEPROPERTY (type , property)  
```  
  
## <a name="arguments"></a>引数  
 *型*  
 データ型の名前を指定します。  
  
 *プロパティ*  
 この関数で取得するデータ型に関する情報の種類を指定します。 *プロパティ*値は次のいずれかになります。  
  
|プロパティ|Description|返される値|  
|--------------|-----------------|--------------------|  
|**AllowsNull**|データ型で NULL 値が許容されるかどうか。|1 = True<br /><br /> 0 = False<br /><br /> NULL = データ型が見つからない|  
|**OwnerId**|データ型の所有者。<br /><br /> 注: スキーマの所有者が必ずしも型の所有者|NULL 以外 = データ型所有者のデータベース ユーザー ID<br /><br /> NULL = サポートされないデータ型、またはデータ型の ID が無効|  
|**[精度]**|データ型の有効桁数。|桁数または文字数<br /><br /> -1 = **xml**または大きな値データ型<br /><br /> NULL = データ型が見つからない|  
|**[スケール]**|データ型の小数点以下桁数。|データ型の小数点以下桁数<br /><br /> NULL = データ型がない**数値**か見つかりません。|  
|**UsesAnsiTrim**|データ型の作成時に ANSI による埋め込みがオンであるかどうか。|1 = True<br /><br /> 0 = False<br /><br /> NULL = データ型が見つからないか、データ型が binary と文字列型のどちらでもない|  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="exceptions"></a>例外  
 エラーが発生した場合、または呼び出し元にオブジェクトの表示権限がない場合は、NULL が返されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーは、ユーザーが所有するまたはをユーザーが許可されているアクセス許可のセキュリティ保護可能なメタデータのみを表示できます。 つまり、オブジェクトに対する権限がユーザーに与えられていない場合、メタデータを生成する組み込み関数 (TYPEPROPERTY など) が NULL を返す可能性があります。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-identifying-the-owner-of-a-data-type"></a>A. データ型の所有者を特定する  
 次の例では、データ型の所有者を返します。  
  
```  
SELECT TYPEPROPERTY(SCHEMA_NAME(schema_id) + '.' + name, 'OwnerId') AS owner_id, name, system_type_id, user_type_id, schema_id  
FROM sys.types;  
```  
  
### <a name="b-returning-the-precision-of-the-tinyint-data-type"></a>B. tinyint データ型の有効桁数を返す  
 次の例では、`tinyint` データ型の有効桁数を返します。  
  
```  
SELECT TYPEPROPERTY( 'tinyint', 'PRECISION');  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-returning-the-precision-of-the-tinyint-data-type"></a>C: は tinyint データ型の有効桁数を返す  
 次の例では、`tinyint` データ型の有効桁数を返します。  
  
```  
SELECT TYPEPROPERTY( 'tinyint', 'PRECISION');  
```  
  
## <a name="see-also"></a>参照  
 [TYPE_ID & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/type-id-transact-sql.md)   
 [TYPE_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/type-name-transact-sql.md)   
 [COLUMNPROPERTY & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/columnproperty-transact-sql.md)   
 [メタデータ関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [ALTER AUTHORIZATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.types & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  


