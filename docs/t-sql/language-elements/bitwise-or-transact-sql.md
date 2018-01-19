---
title: "|(ビットごとの OR)(TRANSACT-SQL) |Microsoft ドキュメント"
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
- '|'
- '|_TSQL'
- Bitwise OR
- bitwise
- OR
dev_langs: TSQL
helpviewer_keywords:
- OR operator
- bitwise OR (|)
- '| (bitwise OR operator)'
ms.assetid: 86a3b87f-9688-4eaf-a552-29f1b01d880a
caps.latest.revision: "43"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 5e77a2e7132b7d32a27b7f5be236d75576cb0fcf
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-bitwise-or-transact-sql"></a>| (ビット演算子 OR) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの中で、バイナリ式に変換された 2 つの指定される整数値に対して、ビットごとの論理和演算を実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```   
expression | expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)整数データ型カテゴリに、または**ビット**、**バイナリ**、または**varbinary**データ型。 *式*はビットごとの演算に対して 2 進数として扱われます。  
  
> [!NOTE]  
>  1 つだけ*式*として指定できる**バイナリ**または**varbinary**ビットごとの演算でのデータ型。  
  
## <a name="result-types"></a>戻り値の型  
 返します、 **int**場合は、入力値**int**、 **smallint**場合は、入力値**smallint**、または**tinyint**場合は、入力値**tinyint**です。  
  
## <a name="remarks"></a>解説  
 ビットごとの | 演算子は、2 つの式の対応するビットを対象にビットごとの論理和演算を実行します。 入力式の中で現在処理の対象にあるビットについて、いずれかのビットまたは両方のビットが 1 の値を持つ場合、結果セットのビットは 1 に設定されます。入力式のビットが両方とも 1 の値を持たない場合、結果セットのビットは 0 に設定されます。  
  
 左と右の式が異なる整数データ型を持つかどうか (たとえば、左側*式*は**smallint**と右*式*は**int**)、小さいデータ型の引数が大きいデータ型に変換します。 この例では、**smallint * * * 式*に変換されますが、 **int**です。  
  
## <a name="examples"></a>使用例  
 次の例を含むテーブルを作成する**int**データ型を元の値を表示して、テーブルに 1 行にします。  
  
```sql  
CREATE TABLE bitwise  
(   
 a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 次のクエリに対してビットごとの OR を実行する、 **a_int_value**と**b_int_value**列です。  
  
```  
SELECT a_int_value | b_int_value  
FROM bitwise;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-----------   
235           
  
(1 row(s) affected)  
```  
  
 170 のバイナリ表現 (**a_int_value**または`A`、下) は`0000 0000 1010 1010`します。 75 のバイナリ表現 (**b_int_value**または`B`、下) は`0000 0000 0100 1011`します。 これら 2 つの値に対してビットごとの OR 演算の実行結果はバイナリ`0000 0000 1110 1011`、これは、10 進数では 235 します。  
  
```  
(A | B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 1110 1011  
```  
  
## <a name="see-also"></a>参照  
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビット処理演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [&#124; = (& a) #40 です。ビットごとの OR 代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


