---
title: CONCAT_WS (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7d7932c1887c82b2a10702f9054706e4cf9bce71
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="concatws-transact-sql"></a>CONCAT_WS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

1 番目の引数で指定された区切り記号で可変の個数の引数を連結します。 (`CONCAT_WS` は "*区切りを使用した連結*" を示します。)

##  <a name="syntax"></a>構文   
```sql
CONCAT_WS ( separator, argument1, argument1 [, argumentN]… ) 
```

## <a name="arguments"></a>引数   
separator  
任意の文字型の式です (`nvarchar`、`varchar`、`nchar`、または `char`)。

argument1, argument2, argument*N*  
任意のデータ型の式です。

## <a name="return-types"></a>戻り値の型
文字列です。 入力に依存する長さおよび型です。

## <a name="remarks"></a>Remarks   
`CONCAT_WS` は、可変数の引数を取得し、最初の引数を区切りとして使用して 1 つの文字列に連結します。 1 つの区切りと最小で 2 つの引数が必要です。それ以外の場合は、エラーが発生します。 すべての引数は、暗黙的に文字列型に変換され、連結されます。 

文字列への暗黙の変換は、データ型変換の既存の規則に従います。 動作とデータ型変換について詳しくは、「[CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)」をご覧ください。

### <a name="treatment-of-null-values"></a>NULL 値の処理方法

`CONCAT_WS` は `SET CONCAT_NULL_YIELDS_NULL {ON|OFF}` 設定を無視します。

すべての引数が null 値の場合、`varchar(1)` 型の空の文字列が返されます。 

null 値は連結時に無視され、区切りを追加しません。 これにより、2 番目のアドレス フィールドなど、空白値であることが多い文字列の連結の一般的なシナリオが容易になります。 例 B をご覧ください。

null 値に区切りを含める必要があるシナリオでは、`ISNULL` 関数を使用する例 C をご覧ください。

## <a name="examples"></a>使用例   

### <a name="a--concatenating-values-with-separator"></a>A.  区切りで値を連結する
次の例では、値を `- ` で区切って、sys.databases テーブルの 3 つの列を連結します。   

```sql
SELECT CONCAT_WS( ' - ', database_id, recovery_model_desc, containment_desc) AS DatabaseInfo
FROM sys.databases;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

|DatabaseInfo |  
|---------|
|1 - SIMPLE - NONE |
|2 - SIMPLE - NONE |
|3 - FULL - NONE |
|4 - SIMPLE - NONE |


### <a name="b--skipping-null-values"></a>B.  Null 値をスキップする
次の例では、引数リスト内の `NULL` 値は無視されます。

```sql
SELECT CONCAT_WS(',','1 Microsoft Way', NULL, NULL, 'Redmond', 'WA', 98052) AS Address;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   

```sql
Address
------------   
1 Microsoft Way,Redmond,WA,98052
```

### <a name="c--generating-csv-file-from-table"></a>C.  テーブルから CSV ファイルを生成する
次の例では、区切りとしてコンマを使用し、復帰文字を追加して列区切り値形式にします。

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

CONCAT_WS は、列の NULL 値を無視します。 一部の列が null 許容の場合は、それを `ISNULL` 関数でラップし、次の例のように既定値を提供します。

```sql
SELECT 
STRING_AGG(CONCAT_WS( ',', database_id, ISNULL(recovery_model_desc,''), ISNULL(containment_desc,'N/A')), char(13)) AS DatabaseInfo
FROM sys.databases;
```

## <a name="see-also"></a>参照
 [CONCAT &#40;Transact-SQL&#41;](../../t-sql/functions/concat-transact-sql.md)  
 [FORMATMESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME &#40;Transact-SQL&#41;](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE &#40;Transact-SQL&#41;](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE &#40;Transact-SQL&#41;](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG &#40;Transact-SQL&#41;](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE &#40;Transact-SQL&#41;](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF &#40;Transact-SQL&#41;](../../t-sql/functions/stuff-transact-sql.md)  
 [TRANSLATE &#40;Transact-SQL&#41;](../../t-sql/functions/translate-transact-sql.md)  
 [文字列関数 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  

