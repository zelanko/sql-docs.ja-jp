---
title: "CONCAT_WS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONCAT_WS
- CONCAT_WS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CONCAT_WS function
ms.assetid: f1375fd7-a2fd-48bf-922a-4f778f0deb1f
caps.latest.revision: 5
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 377db445118e55f1bdeec220f1e6701e9f89706c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="concatws-transact-sql"></a>CONCAT_WS (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-asdb-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-asdb-xxxx-xxx.md)]

1 番目の引数で指定された区切り記号では、可変個の引数を連結します。 (`CONCAT_WS`示す*区切り記号で連結*)。

##  <a name="syntax"></a>構文   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>引数   
separator  
任意の文字型の式です (`nvarchar`、 `varchar`、 `nchar`、または`char`)。

[引数 1]、[引数 2]、引数*N*  
任意の型の式です。

## <a name="return-types"></a>戻り値の型
文字列です。 長さと型は、入力に依存します。

## <a name="remarks"></a>解説   
`CONCAT_WS`可変個の引数を受け取るし、最初の引数を使用して、区切り記号として単一の文字列に連結します。 区切り記号と 2 つの引数の最小値が必要です。それ以外の場合、エラーが発生します。 すべての引数は、文字列型に暗黙的に変換されます、連結してです。 

文字列への暗黙の変換は、データ型変換の既存の規則に従います。 動作とデータの型変換の詳細については、次を参照してください。 [CONCAT (TRANSACT-SQL)](../../t-sql/functions/concat-transact-sql.md)です。

### <a name="treatment-of-null-values"></a>NULL 値の処理方法

`CONCAT_WS`無視、`SET CONCAT_NULL_YIELDS_NULL {ON|OFF}`設定します。

すべての引数が null、空の文字列型の場合`varchar(1)`が返されます。 

Null 値は、連結、時に無視され、区切り記号を追加しません。 これには、多くの場合、2 番目のアドレス フィールドなど、空白の値である必要が文字列の連結の一般的なシナリオが容易になります。 例 B を参照してください。

シナリオでは、null 値が、区切り記号に含まれている必要がある場合は、例 C を使用して参照してください、`ISNULL`関数。

## <a name="examples"></a>使用例   

### <a name="a--concatenating-values-with-separator"></a>A.  区切り記号で値を連結します。
次の例は、値を分離すること、sys.databases テーブルから 3 つの列を連結、`- `です。   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1-単純な - なし |
|2-シンプル - なし |
|3 - フル - なし |
|4-シンプル - なし |


### <a name="b--skipping-null-values"></a>B.  NULL 値をスキップしています
次の例では無視`NULL`引数リスト内の値。

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>C.  テーブルから CSV ファイルを生成します。
次の例では、区切り記号としてコンマを使用し、列区切り形式で結果は復帰文字を追加します。

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, recovery_model_desc, containment_desc), char(13)) AS DatabaseInfo
FROM sys.databases
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
DatabaseInfo
------------   
1,SIMPLE,NONE
2,SIMPLE,NONE
3,FULL,NONE 
4,SIMPLE,NONE 
```

CONCAT_WS 列の NULL 値は無視されます。 一部の列が null 許容で場合にそれを囲み`ISNULL`機能し、次の例のように既定値を指定します。

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>参照
[文字列関数 (TRANSACT-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
[CONCAT (TRANSACT-SQL)](../../t-sql/functions/concat-transact-sql.md)      


