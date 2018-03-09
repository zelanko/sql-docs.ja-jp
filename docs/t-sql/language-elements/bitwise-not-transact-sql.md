---
title: "~ (ビット演算子 NOT) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/10/2017
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
f1_keywords:
- ~_TSQL
- bitwise
- NOT
- ~
- Bitwise NOT
dev_langs:
- TSQL
helpviewer_keywords:
- NOT keyword
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: 02da8016-f6c0-41ae-8d59-33eaa02bfc95
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bc129a0a62c393cb8aee03edca3e0c2b567f9488
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="-bitwise-not-transact-sql"></a>~ (ビット演算子 NOT) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  整数値に対してビットごとの論理否定演算を実行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
~ expression  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)、整数データ型カテゴリのデータ型のいずれかの**ビット**、または**バイナリ**または**varbinary**データ型。 *式*はビットごとの演算に対して 2 進数として扱われます。  
  
> [!NOTE]  
>  1 つだけ*式*として指定できる**バイナリ**または**varbinary**ビットごとの演算でのデータ型。  
  
## <a name="result-types"></a>戻り値の型  
 **int**場合は、入力値**int**です。  
  
 **smallint**場合は、入力値**smallint**です。  
  
 **tinyint**場合は、入力値**tinyint**です。  
  
 **ビット**場合は、入力値**ビット**です。  
  
## <a name="remarks"></a>解説  
 **~** ビットごとの演算子が論理否定演算を実行用、*式*、さらに、各ビットです。 場合*式*値が 0 の場合の結果セット内のビットが 1 に設定されます。 それ以外の場合、結果のビットがオフになって値の 0 にします。 つまり、1 は 0 に、0 は 1 に変更されます。  
  
> [!IMPORTANT]  
>  どのような種類のビットごとの演算を実行する場合でも、演算の中で使用される式の記憶域の長さが重要になります。 値を格納するときは、式のデータ型と同じバイト数を使用するようにしてください。 たとえば、同様の 5 つの 10 進値を格納する、 **tinyint**、 **smallint**、または**int**バイト数が異なると共に格納されている値を生成: **tinyint** 1 バイトを使用してデータの格納**smallint** 2 (バイト単位) を使用してデータを格納および**int** 4 バイトを使用してデータを格納します。 したがってでビットごとの演算を実行する、 **int** 10 進値は、直接バイナリまたは 16 進数の変換を使用して異なる結果を生成できる場合は特に、  **~**  (ビットごとの NOT) 演算子を使用します。 また、長さが短い方の変数に対してビットごとの NOT 演算が実行される場合があります。 この場合は、短い長さが長いデータ型の変数に変換するときに、上位 8 ビットのビット可能性がありますしない設定適切な値にします。 短いデータ型を長いデータ型に変換し、その結果に対して NOT 演算を実行するようにしてください。  
  
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
  
 次のクエリ実行ではありません、ビットごとの`a_int_value`と`b_int_value`列です。  
  
```  
SELECT ~ a_int_value, ~ b_int_value  
FROM bitwise;  
```  
  
 Here is the result set:  
  
```  
--- ---   
-171  -76   
  
(1 row(s) affected)  
```  
  
 170 のバイナリ表現 (`a_int_value`または`A`) は`0000 0000 1010 1010`します。 この値に対してビットごとの NOT 演算を実行すると、結果はバイナリで `1111 1111 0101 0101`、10 進数では -171 になります。 75 をバイナリで表すと `0000 0000 0100 1011` になります。 演算を実行する操作ではなく生成`1111 1111 1011 0100`、これは、10 進-76 になります。  
  
```  
 (~A)     
         0000 0000 1010 1010  
         -------------------  
         1111 1111 0101 0101  
(~B)     
         0000 0000 0100 1011  
         -------------------  
         1111 1111 1011 0100  
```  
  
 
## <a name="see-also"></a>参照  
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [ビット処理演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  


