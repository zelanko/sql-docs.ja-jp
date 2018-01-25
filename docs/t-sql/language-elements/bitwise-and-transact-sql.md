---
title: "&amp;(ビット演算 AND)(TRANSACT-SQL) |Microsoft ドキュメント"
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
- bitwise
- '&'
- '&_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- AND, bitwise AND
- '& (bitwise AND)'
- bitwise AND (&)
ms.assetid: 20275755-4fa7-47b1-a9be-ac85606d63b0
caps.latest.revision: "42"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 094c127434f2339a4a3e977c4455ca6ce904ab01
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="amp-bitwise-and-transact-sql"></a>&amp;(ビット演算 AND)(TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  2 つの整数値の間でビットごとの論理積演算を実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
expression & expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)の整数のデータ型カテゴリのデータ型のいずれかまたは**ビット**、または**バイナリ**または**varbinary**データ型。 *式*はビットごとの演算に対して 2 進数として扱われます。  
  
> [!NOTE]  
>  1 つだけにビットごとの演算で*式*として指定できる**バイナリ**または**varbinary**データ型。  
  
## <a name="result-types"></a>戻り値の型  
 **int**場合は、入力値**int**です。  
  
 **smallint**場合は、入力値**smallint**です。  
  
 **tinyint**場合は、入力値**tinyint**または**ビット**です。  
  
## <a name="remarks"></a>解説  
 **&** ビットごとの演算子は、対応する各ビット両方の式の 2 つの式の間でビットごとの論理 AND を実行します。 入力式の中で現在処理の対象にあるビットについて、両方のビットが 1 という値を持つ場合だけ、結果セットのビットは 1 に設定されます。それ以外の場合、結果は 0 に設定されます。  
  
 左と右の式が異なる整数データ型を持つかどうか (たとえば、左側*式*は**smallint**と右*式*は**int**)、小さいデータ型の引数が大きいデータ型に変換します。 ここで、**smallint * * * 式*に変換されます、 **int**です。  
  
## <a name="examples"></a>使用例  
 次の例を使用してテーブルを作成、 **int**データ値を格納する型で、1 行に 2 つの値を挿入します。  
  
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
  
 このクエリの実行の間でビットごとの AND、`a_int_value`と`b_int_value`列です。  
  
```  
SELECT a_int_value & b_int_value  
FROM bitwise;  
GO  
```  
  
 Here is the result set:  
  
```  
-----------   
10            
  
(1 row(s) affected)  
```  
  
 170 のバイナリ表現 (`a_int_value`または`A`) は`0000 0000 1010 1010`します。 75 のバイナリ表現 (`b_int_value`または`B`) は`0000 0000 0100 1011`します。 この 2 つの値に対してビットごとの論理積演算を実行すると、結果はバイナリで `0000 0000 0000 1010`、10 進数では 10 になります。  
  
```  
(A & B)  
0000 0000 1010 1010  
0000 0000 0100 1011  
-------------------  
0000 0000 0000 1010  
```  
  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビット処理演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-operators-transact-sql.md)   
 [& = (& a) #40 です。ビットごとの AND 代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


