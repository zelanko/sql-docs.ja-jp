---
title: "^ (ビットごとの排他的 OR) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ^_TSQL
- Bitwise Exclusive OR
- Exclusive
- ^
- bitwise
- OR
dev_langs: TSQL
helpviewer_keywords:
- ^ (bitwise exclusive OR operator)
- OR operator
- exclusive OR mathematical operations
- bitwise exclusive OR (^)
ms.assetid: f38f0ad4-46d0-40ea-9851-0f928fda5293
caps.latest.revision: "44"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4923d20bdeb7e625157a47c0f70e685895c41550
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="-bitwise-exclusive-or-transact-sql"></a>^ (ビットごとの排他的 OR) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの整数の間でビットごとの排他的 OR 演算を実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression ^ expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)、整数データ型カテゴリのデータ型のいずれかのまたは**ビット**、または**バイナリ**または**varbinary**データ型。 *式*はビットごとの演算に対して 2 進数として扱われます。  
  
> [!NOTE]  
>  1 つだけ*式*として指定できる**バイナリ**または**varbinary**ビットごとの演算でのデータ型。  
  
## <a name="result-types"></a>戻り値の型  
 **int**場合は、入力値**int**です。  
  
 **smallint**場合は、入力値**smallint**です。  
  
 **tinyint**場合は、入力値**tinyint**です。  
  
## <a name="remarks"></a>解説  
 **^** ビットごとの演算子は、対応する各ビット両方の式の 2 つの式の間の論理排他的 OR 演算を実行します。 入力式で現在処理対象となっているビットについて、両方ではなくいずれか一方のビットだけが 1 の場合、結果セットのビットは 1 に設定されます。 両方のビットが 0 または 1 の場合、結果セットのビットはクリアされて 0 になります。  
  
 左と右の式が異なる整数データ型を持つかどうか (たとえば、左側*式*は**smallint**と右*式*は**int**)、小さいデータ型の引数が大きいデータ型に変換します。 ここで、 **smallint***式*に変換されます、 **int**です。  
  
## <a name="examples"></a>使用例  
 次の例を使用してテーブルを作成、 **int**データを元の値を格納する型で、1 行に 2 つの値を挿入します。  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 次のクエリでは、`a_int_value` 列と `b_int_value` 列との間でビットごとの排他的論理 OR を実行します。  
  
```  
SELECT a_int_value ^ b_int_value  
FROM bitwise;  
GO  
```  
  
 Here is the result set:  
  
```  
-----------   
225           
  
(1 row(s) affected)  
```  
  
 170 のバイナリ表現 (`a_int_value`または`A`) は`0000 0000 1010 1010`します。 75 のバイナリ表現 (`b_int_value`または`B`) は`0000 0000 0100 1011`します。 これら 2 つの値のビットごとの排他的 or 演算の実行結果はバイナリ`0000 0000 1110 0001`225 の 10 進数であります。  
  
```  
(A ^ B)     
         0000 0000 1010 1010  
         0000 0000 0100 1011  
         -------------------  
         0000 0000 1110 0001  
```  
  

  
## <a name="see-also"></a>参照  
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビット処理演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [^ = (& a) #40 です。ビットごとの排他的 OR 代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


