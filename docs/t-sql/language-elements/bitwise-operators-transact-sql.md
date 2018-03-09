---
title: "ビット処理演算子 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- operators [Transact-SQL], bitwise
- bitwise operators
- bit manipulations
ms.assetid: 2b994cf5-2daa-438a-b8c7-4bd8d451ac8d
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: b0706080c0a878987fab8d2cc5f0c1677f43309b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="bitwise-operators-transact-sql"></a>ビットごとの演算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  ビットごとの演算子は、整数型に分類されるデータ型を持つ 2 つの式に対してビット操作を実行します。  
  ビットごとの演算子はバイナリ ビットを 2 つの整数値を変換、AND を実行 OR、または操作の結果を生成し、ビットごとのではありません。 結果を整数に変換します。  
  
  たとえば、整数 170 はバイナリ 1010 1010 に変換します。
バイナリ 0100 1011 75 の整数に変換します。

|演算子 (operator)|ビットごとの演算|
|---- |---- |
|[AND] <br> 任意の位置のビットが 1 の場合は、結果は 1 です。 |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 0000 1010 =  10 |
|または <br> 任意の場所にどちらかのビットが 1 の場合、結果は 1 です。 |1010 1010 = 170 <br>0100 1011 =  75 <br>-----------------  <br> 1110 1011 = 235|
|[NOT]  <br> ビットのすべての場所にあるビット値を反転させます。 |1010 1010 = 170 <br>----------------- <br>  0101 0101 =   85 |
  
次のトピックを参照してください。   
* [& &#40;です。ビットごとの AND &#41;](../../t-sql/language-elements/bitwise-and-transact-sql.md)  
* [& = (& a) #40 です。ビットごとの AND 代入 &#41;](../../t-sql/language-elements/bitwise-and-equals-transact-sql.md)   
* [&#124;です。&#40;です。ビットごとの OR &#41;](../../t-sql/language-elements/bitwise-or-transact-sql.md)  
* [&#124; = (& a) #40 です。ビットごとの OR 代入 &#41;](../../t-sql/language-elements/bitwise-or-equals-transact-sql.md)   
* [^ (& a) #40 です。ビットごとの排他的 OR &#41;](../../t-sql/language-elements/bitwise-exclusive-or-transact-sql.md)  
* [^ = (& a) #40 です。ビットごとの排他的 OR 代入 &#41;](../../t-sql/language-elements/bitwise-exclusive-or-equals-transact-sql.md)  
* [~ &#40;です。ビットごとの NOT &#41;](../../t-sql/language-elements/bitwise-not-transact-sql.md)  
  
 ビットごとの演算子のオペランドが整数またはバイナリ文字列データ型カテゴリのデータ型のいずれかを指定できます (を除き、**イメージ**データ型)、両方のオペランドがバイナリ文字列のデータ型のいずれかにすることはできませんデータ型に分類します。 次の表は、サポートされているオペランドのデータ型を示します。  
  
|左オペランド|右オペランド|  
|------------------|-------------------|  
|[[バイナリ]](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**、 **smallint**、または**tinyint**|  
|[bit](../../t-sql/data-types/bit-transact-sql.md)|**int**、 **smallint**、 **tinyint**、または**ビット**|  
|[int](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**、 **smallint**、 **tinyint**、**バイナリ**、または**varbinary**|  
|[smallint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**、 **smallint**、 **tinyint**、**バイナリ**、または**varbinary**|  
|[tinyint](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)|**int**、 **smallint**、 **tinyint**、**バイナリ**、または**varbinary**|  
|[varbinary](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|**int**、 **smallint**、または**tinyint**|  
  
## <a name="see-also"></a>参照  
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)   
  
